---
title: IDebugExpressionAvaliador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluator
helpviewer_keywords:
- IDebugExpressionEvaluator interface
ms.assetid: 0636d8c3-625a-49fa-94b6-516f22b7e1bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e8dd910e4edc110abb40dde14b4cb85ff54a70a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729378"
---
# <a name="idebugexpressionevaluator"></a>IDebugExpressionEvaluator
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [Avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [Amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

Esta interface representa o avaliador de expressão.

## <a name="syntax"></a>Sintaxe

```
IDebugExpressionEvaluator : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
O avaliador de expressão deve implementar essa interface.

## <a name="notes-for-callers"></a>Observações para chamadores
Para obter essa interface, instanciar `CoCreateInstance` o avaliador de expressão através do método utilizando o ID de classe (CLSID) do avaliador. Veja o Exemplo.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
A tabela a seguir `IDebugExpressionEvaluator`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Analisar](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)|Converte uma seqüência de expressão em uma expressão analisada.|
|[GetMethodProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md)|Obtém as variáveis locais, argumentos e outras propriedades de um método.|
|[GetMethodLocationProperty](../../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodlocationproperty.md)|Converte um local de método e deslocamento em um endereço de memória.|
|[SetLocale](../../../extensibility/debugger/reference/idebugexpressionevaluator-setlocale.md)|Determina qual idioma usar para criar resultados imprimíveis.|
|[SetRegistryRoot](../../../extensibility/debugger/reference/idebugexpressionevaluator-setregistryroot.md)|Define a raiz do registro. Usado para depuração lado a lado.|

## <a name="remarks"></a>Comentários
Em uma situação típica, o mecanismo de depuração (DE) instancia o avaliador de expressão (EE) como resultado de uma chamada para [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Como o DE conhece o idioma e o fornecedor do EE que deseja usar, o DE obtém o CLSID do `GetEEMetric`EE do registro (os [Ajudantes do SDK para depuração,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , ajuda com essa recuperação).

Depois que o EE é instanciado, o DE chama [Parse](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para analisar a expressão e armazená-la em um objeto [IDebugParsedExpression.](../../../extensibility/debugger/reference/idebugparsedexpression.md) Mais tarde, uma chamada para [AssessSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) avalia a expressão.

## <a name="requirements"></a>Requisitos
Cabeçalho: ee.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Exemplo
Este exemplo mostra como instanciar o avaliador de expressão dado a um provedor de símbolos e um endereço no código-fonte. Este exemplo usa `GetEEMetric`uma função, da biblioteca [SDK Helpers for Debugging,](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) dbgmetric.lib.

```cpp
IDebugExpressionEvaluator GetExpressionEvaluator(IDebugSymbolProvider pSymbolProvider,
                                                 IDebugAddress *pSourceAddress)
{
    // This is typically defined globally but is specified here just
    // for this example.
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";

    IDebugExpressionEvaluator *pEE = NULL;
    if (pSymbolProvider != NULL && pSourceAddress != NULL) {
        HRESULT hr         = S_OK;
        GUID  languageGuid = { 0 };
        GUID  vendorGuid   = { 0 };

        hr = pSymbolProvider->GetLanguage(pSourceAddress,
                                          &languageGuid,
                                          &vendorGuid);
        if (SUCCEEDED(hr)) {
            CLSID clsidEE = { 0 };
            CComPtr<IDebugExpressionEvaluator> spExpressionEvaluator;
            // Get the expression evaluator's CLSID from the registry.
            ::GetEEMetric(languageGuid,
                          vendorGuid,
                          metricCLSID,
                          &clsidEE,
                          strRegistrationRoot);
            if (!IsEqualGUID(clsidEE,GUID_NULL)) {
                // Instantiate the expression evaluator.
                spExpressionEvaluator.CoCreateInstance(clsidEE);
            }
            if (spExpressionEvaluator != NULL) {
                pEE = spExpressionEvaluator.Detach();
            }
        }
    }
    return pEE;
}
```

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)
- [IDebugParsedExpression](../../../extensibility/debugger/reference/idebugparsedexpression.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
