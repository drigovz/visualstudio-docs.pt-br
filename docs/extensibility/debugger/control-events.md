---
title: Eventos de Controle | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 0fc63484-5fb6-4887-9ea4-1905b459ca9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc2c3ad9c9b63923bdf2f107e7bc582f3c76cd62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739092"
---
# <a name="control-events"></a>Eventos de controle
Você deve enviar eventos durante a execução controlada do seu programa. Todos os eventos são enviados usando a interface [IDebugEvent2](../../extensibility/debugger/reference/idebugevent2.md) e têm atributos que exigem que você implemente o método [IDebugEvent2::GetAttributes.](../../extensibility/debugger/reference/idebugevent2-getattributes.md)

## <a name="additional-methods"></a>Métodos adicionais
 Alguns eventos exigem a implementação de métodos adicionais, da seguinte forma:

- O envio da interface [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) quando o mecanismo de depuração (DE) é inicializado requer que você implemente o método [IDebugEngineCreateEvent2::GetEngine.](../../extensibility/debugger/reference/idebugenginecreateevent2-getengine.md)

- O controle de execução requer a implementação de eventos de controle como as interfaces [IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md) e[IDebugStepCompleteEvent2.](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) **IDebugBreakEvent2** é necessário apenas para quebras assíncronas.

- Entrar em funções requer a implementação da interface [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) e seus métodos.

  Eventos derivados de breakpoints requerem a implementação dos métodos [IDebugBreakpointErrorEvent2,](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)e [IDebugBreakpointBoundEvent2,](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) bem como os métodos [IDebugBreakpointBoundEvent2:GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [EnumBoundBreakpoints.](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)

  A avaliação de expressão assíncrona exige que você implemente a interface [IDebugExpressionCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) e seus métodos [IDebugExpressionCompleteEvent2::GetExpression](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)[e GetResult.](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)

  Eventos síncronos requerem a implementação do método [IDebugEngine2::ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

  Para que o motor escreva a saída de estilo de string, você deve implementar o método [IDebugOutput2Event2::GetString.](../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)

## <a name="see-also"></a>Confira também
- [Controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
