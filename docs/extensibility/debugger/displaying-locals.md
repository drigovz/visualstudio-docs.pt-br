---
title: Exibindo locais | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, displaying locals
ms.assetid: 62264cec-845b-4233-aed7-0b038fa79250
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d44b276aeb9c6acb0ef34cc186662d49246de7d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738938"
---
# <a name="display-locals"></a>Mostrar locais
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 A execução sempre ocorre no contexto de um método, também conhecido como método de contenção ou método atual. Quando a execução é pausada, o Visual Studio chama o mecanismo de depuração (DE) para obter uma lista de variáveis e argumentos locais, chamados coletivamente de locais do método. Visual Studio exibe esses locais e seus valores na janela **locais.**

 Para exibir locais, o DE chama o método [GetMethodProperty](../../extensibility/debugger/reference/idebugexpressionevaluator-getmethodproperty.md) pertencente ao EE e fornece um contexto de avaliação, ou seja, um provedor de símbolos (SP), o endereço de execução atual e um objeto de encadernação. Para obter mais informações, consulte [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md). Se a chamada for `IDebugExpressionEvaluator::GetMethodProperty` bem-sucedida, o método retorna um objeto [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) que representa o método que contém o endereço de execução atual.

 O DE chama [enumChildren](../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) para obter um objeto [IEnumDebugPropertyInfo2,](../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) que é filtrado para retornar apenas os locais e enumerado para produzir uma lista de estruturas [DEBUG_PROPERTY_INFO.](../../extensibility/debugger/reference/debug-property-info.md) Cada estrutura contém o nome, o tipo e o valor de um local. O tipo e o valor são armazenados como strings formatados, adequados para exibição. O nome, o tipo e o valor são normalmente exibidos juntos em uma linha da janela **Locals.**

> [!NOTE]
> As janelas **QuickWatch** e **Watch** também exibem variáveis com o mesmo formato de nome, valor e tipo. No entanto, esses valores são obtidos ligando para [GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) em vez de `IDebugProperty2::EnumChildren`.

## <a name="in-this-section"></a>Nesta seção
 [Implementação amostral de moradores](../../extensibility/debugger/sample-implementation-of-locals.md) Usa exemplos para passar pelo processo de implementação de moradores locais.

## <a name="related-sections"></a>Seções relacionadas
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md) Explica que quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE), ele passa por três argumentos.

## <a name="see-also"></a>Confira também
 [Escreva um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
