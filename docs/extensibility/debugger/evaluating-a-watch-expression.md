---
title: Avaliando uma expressão de relógio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, watch expressions
- watch expressions
ms.assetid: 8317cd52-6fea-4e8f-a739-774dc06bd44b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a239e430338e88a0be4bc35ad1c357925f7d8f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738860"
---
# <a name="evaluate-a-watch-expression"></a>Avalie uma expressão de relógio
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Quando o Visual Studio está pronto para exibir o valor de uma expressão de relógio, ele chama [AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md), que por sua vez chama [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md). Este processo produz um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que contém o valor e o tipo da expressão.

Nesta implementação `IDebugParsedExpression::EvaluateSync`de , a expressão é analisado e avaliado ao mesmo tempo. Esta implementação executa as seguintes tarefas:

1. Analisa e avalia a expressão para produzir um objeto genérico que detém o valor e seu tipo. Em C#, isso é `object` representado como um tempo em `VARIANT`C++, isso é representado como um .

2. Instancia uma classe `CValueProperty` (chamada neste exemplo) `IDebugProperty2` que implementa a interface e armazena na classe o valor a ser devolvido.

3. Retorna `IDebugProperty2` a interface `CValueProperty` do objeto.

## <a name="managed-code"></a>Código gerenciado
Esta é uma `IDebugParsedExpression::EvaluateSync` implementação do código gerenciado. O método `Tokenize` auxiliar analisa a expressão em uma árvore de análise. A função `EvalToken` auxiliar converte o token em um valor. A função `FindTerm` auxiliar atravessa recursivamente a árvore `EvalToken` de análise, solicitando cada nó representando um valor e aplicando quaisquer operações (adição ou subtração) na expressão.

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT EvaluateSync(
            uint evalFlags,
            uint timeout,
            IDebugSymbolProvider provider,
            IDebugAddress address,
            IDebugBinder binder,
            string resultType,
            out IDebugProperty2 result)
        {
            HRESULT retval = COM.S_OK;
            this.evalFlags = evalFlags;
            this.timeout = timeout;
            this.provider = provider;
            this.address = address;
            this.binder = binder;
            this.resultType = resultType;

            try
            {
                IDebugField field = null;
                // Tokenize, then parse.
                tokens = Tokenize(expression);
                result = new CValueProperty(
                        expression,
                        (int) FindTerm(EvalToken(tokens[0], out field),1),
                        field,
                        binder);
            }
            catch (ParseException)
            {
                result = new CValueProperty(expression, "Huh?");
                retval = COM.E_INVALIDARG;
            }
            return retval;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código não gerenciado
Esta é uma `IDebugParsedExpression::EvaluateSync` implementação do código não gerenciado. A função `Evaluate` auxiliar analisa e avalia a expressão, `VARIANT` devolvendo uma retenção do valor resultante. A função `VariantValueToProperty` auxiliar empacota o `VARIANT` em um `CValueProperty` objeto.

```cpp
STDMETHODIMP CParsedExpression::EvaluateSync(
    in  DWORD                 evalFlags,
    in  DWORD                 dwTimeout,
    in  IDebugSymbolProvider* pprovider,
    in  IDebugAddress*        paddress,
    in  IDebugBinder*         pbinder,
    in  BSTR                  bstrResultType,
    out IDebugProperty2**     ppproperty )
{
    // dwTimeout parameter is ignored in this implementation.
    if (pprovider == NULL)
        return E_INVALIDARG;

    if (paddress == NULL)
        return E_INVALIDARG;

    if (pbinder == NULL)
        return E_INVALIDARG;

    if (ppproperty == NULL)
        return E_INVALIDARG;
    else
        *ppproperty = 0;

    HRESULT hr;
    VARIANT value;
    BSTR    bstrErrorMessage = NULL;
    hr = ::Evaluate( pprovider,
                     paddress,
                     pbinder,
                     m_expr,
                     &bstrErrorMessage,
                     &value );
    if (hr != S_OK)
    {
        if (bstrErrorMessage == NULL)
            return hr;

        //we can display better messages ourselves.
        HRESULT hrLocal = S_OK;
        VARIANT varType;
        VARIANT varErrorMessage;

        VariantInit( &varType );
        VariantInit( &varErrorMessage );
        varErrorMessage.vt      = VT_BSTR;
        varErrorMessage.bstrVal = bstrErrorMessage;

        CValueProperty* valueProperty = new CValueProperty();
        if (valueProperty != NULL)
        {
            hrLocal = valueProperty->Init(m_expr, varType, varErrorMessage);
            if (SUCCEEDED(hrLocal))
            {
                hrLocal = valueProperty->QueryInterface( IID_IDebugProperty2,
                        reinterpret_cast<void**>(ppproperty) );
            }
        }

        VariantClear(&varType);
        VariantClear(&varErrorMessage); //frees BSTR
        if (!valueProperty)
            return hr;
        valueProperty->Release();
        if (FAILED(hrLocal))
            return hr;
    }
    else
    {
        if (bstrErrorMessage != NULL)
            SysFreeString(bstrErrorMessage);

        hr = VariantValueToProperty( pprovider,
                                     paddress,
                                     pbinder,
                                     m_radix,
                                     m_expr,
                                     value,
                                     ppproperty );
        VariantClear(&value);
        if (FAILED(hr))
            return hr;
    }

    return S_OK;
}
```

## <a name="see-also"></a>Confira também
- [Avalie a expressão da janela do relógio](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Implementação amostral da avaliação de expressão](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md)
