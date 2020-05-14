---
title: Implementação amostral de locais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], local variables
- expression evaluation, local variables
ms.assetid: 66a2e00a-f558-4e87-96b8-5ecf5509e04c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6b70e0f9091d40ed6b5fc44934606f42ccd84b21
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713082"
---
# <a name="sample-implementation-of-locals"></a>Implementação amostral de moradores
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A seguir está uma visão geral de como o Visual Studio obtém os locais para um método a partir do avaliador de expressão (EE):

1. O Visual Studio chama o [GetDebugProperty](../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) do mecanismo de depuração (DE) para obter um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa todas as propriedades do quadro de pilha, incluindo os locais.

2. `IDebugStackFrame2::GetDebugProperty`chama [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) para obter um objeto que descreva o método no qual o ponto de ruptura aconteceu. O DE fornece um provedor de símbolos[(IDebugSymbolProvider),](../../extensibility/debugger/reference/idebugsymbolprovider.md)um endereço[(IDebugAddress)](../../extensibility/debugger/reference/idebugaddress.md)e um binder[(IDebugBinder).](../../extensibility/debugger/reference/idebugbinder.md)

3. `IDebugExpressionEvaluator::GetMethodProperty`chama [GetContainerField](../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md) com `IDebugAddress` o objeto fornecido para obter um [IDebugContainerField](../../extensibility/debugger/reference/idebugcontainerfield.md) que representa o método que contém o endereço especificado.

4. A `IDebugContainerField` interface é consultada para a interface [IDebugMethodField.](../../extensibility/debugger/reference/idebugmethodfield.md) É essa interface que dá acesso aos locais do método.

5. `IDebugExpressionEvaluator::GetMethodProperty`instancia uma classe `CFieldProperty` (chamada na amostra) que executa a `IDebugProperty2` interface para representar os locais do método. O `IDebugMethodField` objeto é `CFieldProperty` colocado neste `IDebugSymbolProvider`objeto `IDebugAddress`junto `IDebugBinder` com os objetos e objetos.

6. Quando `CFieldProperty` o objeto é inicializado, o `IDebugMethodField` [GetInfo](../../extensibility/debugger/reference/idebugfield-getinfo.md) é chamado ao objeto para obter uma estrutura [FIELD_INFO](../../extensibility/debugger/reference/field-info.md) que contém todas as informações exibidas sobre o método em si.

7. `IDebugExpressionEvaluator::GetMethodProperty`retorna `CFieldProperty` o objeto `IDebugProperty2` como um objeto.

8. O Visual Studio chama [EnumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) no objeto retornado `IDebugProperty2` com o filtro `guidFilterLocalsPlusArgs`, que retorna um objeto [IEnumDebugPropertyInfo2](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) contendo os locais do método. Esta enumeração é preenchida por chamadas para [EnumLocals](../../extensibility/debugger/reference/idebugmethodfield-enumlocals.md) e [EnumArguments](../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md).

9. O Visual Studio chama [o Next](../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) para obter uma estrutura [DEBUG_PROPERTY_INFO](../../extensibility/debugger/reference/debug-property-info.md) para cada local. Esta estrutura contém um `IDebugProperty2` ponteiro para uma interface para um local.

10. O Visual Studio chama [getPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para cada local para obter o nome, valor e tipo do local. Essas informações são exibidas na janela **Locais.**

## <a name="in-this-section"></a>Nesta seção
 [Implementar getmethodproperty](../../extensibility/debugger/implementing-getmethodproperty.md) Descreve uma implementação do [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md).

 [Enumerar moradores](../../extensibility/debugger/enumerating-locals.md) Descreve como o mecanismo de depuração (DE) faz uma chamada para enumerar variáveis ou argumentos locais.

 [Obtenha propriedades locais](../../extensibility/debugger/getting-local-properties.md) Descreve como o DE faz uma chamada para obter o nome, o tipo e o valor de um ou mais locais.

 [Obter valores locais](../../extensibility/debugger/getting-local-values.md) Discute-se a obtenção do valor do local, que requer os serviços de um objeto de aglutinante dado pelo contexto de avaliação.

 [Avalie os locais](../../extensibility/debugger/evaluating-locals.md) Explica como os locais são avaliados.

## <a name="related-sections"></a>Seções relacionadas
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md) Fornece os argumentos que são passados quando o DE chama o avaliador de expressão (EE).

 [Amostra de MyCEE](https://msdn.microsoft.com/library/624a018b-9179-402f-9d48-3aec87b48f4f) Demonstra uma abordagem de implementação para criar um avaliador de expressão para a língua MyC.

## <a name="see-also"></a>Confira também
- [Exibindo locais](../../extensibility/debugger/displaying-locals.md)
