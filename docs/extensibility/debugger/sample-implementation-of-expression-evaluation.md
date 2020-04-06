---
title: Implementação amostral de avaliação de expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators
- debugging [Debugging SDK], expression evaluators
- expression evaluation, examples
ms.assetid: 2a5f04b8-6c65-4232-bddd-9093653a22c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf994a61ed9283463cd01aa468018f6acce5e209
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713105"
---
# <a name="sample-implementation-of-expression-evaluation"></a>Implementação amostral da avaliação de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Para uma expressão da janela **do relógio,** o Visual Studio chama [o ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para produzir um objeto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) `IDebugExpressionContext2::ParseText`instancia um avaliador de expressão (EE) e chama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para obter um objeto [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

 O `IDebugExpressionEvaluator::Parse` executa as seguintes tarefas:

1. [Somente C++] Analisa a expressão para procurar erros.

2. Instancia uma classe `CParsedExpression` (chamada neste exemplo) que executa a `IDebugParsedExpression` interface e armazena na classe a expressão a ser analisado.

3. Retorna `IDebugParsedExpression` a interface `CParsedExpression` do objeto.

> [!NOTE]
> Nos exemplos que se seguem e na amostra MyCEE, o avaliador de expressão não separa o parsing da avaliação.

## <a name="managed-code"></a>Código gerenciado
 O código a seguir `IDebugExpressionEvaluator::Parse` mostra uma implementação do código gerenciado. Esta versão do método adia a análise para [AssessSync,](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) pois o código para análise também avalia ao mesmo tempo (ver [Avaliar uma expressão de relógio](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```csharp
namespace EEMC
{
    public class CParsedExpression : IDebugParsedExpression
    {
        public HRESULT Parse(
                string                 expression,
                uint                   parseFlags,
                uint                   radix,
            out string                 errorMessage,
            out uint                   errorPosition,
            out IDebugParsedExpression parsedExpression)
        {
            errorMessage = "";
            errorPosition = 0;

            parsedExpression =
                new CParsedExpression(parseFlags, radix, expression);
            return COM.S_OK;
        }
    }
}
```

## <a name="unmanaged-code"></a>Código não gerenciado
O código a seguir `IDebugExpressionEvaluator::Parse` é uma implementação em código não gerenciado. Este método chama uma `Parse`função auxiliar, para analisar a expressão e verificar se há erros, mas este método ignora o valor resultante. A avaliação formal é adiada para [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) onde a expressão é analisado enquanto é avaliada (ver [Avaliar uma expressão de relógio](../../extensibility/debugger/evaluating-a-watch-expression.md)).

```cpp
STDMETHODIMP CExpressionEvaluator::Parse(
        in    LPCOLESTR                 pszExpression,
        in    PARSEFLAGS                flags,
        in    UINT                      radix,
        out   BSTR                     *pbstrErrorMessages,
        inout UINT                     *perrorCount,
        out   IDebugParsedExpression  **ppparsedExpression
    )
{
    if (pbstrErrorMessages == NULL)
        return E_INVALIDARG;
    else
        *pbstrErrormessages = 0;

    if (pparsedExpression == NULL)
        return E_INVALIDARG;
    else
        *pparsedExpression = 0;

    if (perrorCount == NULL)
        return E_INVALIDARG;

    HRESULT hr;
    // Look for errors in the expression but ignore results
    hr = ::Parse( pszExpression, pbstrErrorMessages );
    if (hr != S_OK)
        return hr;

    CParsedExpression* pparsedExpr = new CParsedExpression( radix, flags, pszExpression );
    if (!pparsedExpr)
        return E_OUTOFMEMORY;

    hr = pparsedExpr->QueryInterface( IID_IDebugParsedExpression,
                                      reinterpret_cast<void**>(ppparsedExpression) );
    pparsedExpr->Release();

    return hr;
}
```

## <a name="see-also"></a>Confira também
- [Avalie a expressão da janela do relógio](../../extensibility/debugger/evaluating-a-watch-window-expression.md)
- [Avalie uma expressão de relógio](../../extensibility/debugger/evaluating-a-watch-expression.md)
