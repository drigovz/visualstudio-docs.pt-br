---
title: Tipos de eventos suportados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], supported events
ms.assetid: a3c0386d-551e-4734-9a0c-368d1c2e6671
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 94e26897c50fd7e10a8b831655610848cb93043f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712807"
---
# <a name="supported-event-types"></a>Tipos de eventos suportados
A depuração do Visual Studio atualmente suporta os seguintes tipos de eventos:

- Eventos assíncronos

   Notifique o Gerenciador de Depuração de Sessão (SDM) e o IDE de que o estado do aplicativo que está sendo depurado está mudando. Esses eventos são processados à vontade da SDM e do IDE. Nenhuma resposta é enviada ao mecanismo de depuração (DE) assim que o evento for processado. As interfaces [IDebugOutput2](../../extensibility/debugger/reference/idebugoutputstringevent2.md) e [IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md) são exemplos de eventos assíncronos.

- Eventos síncronos

   Notifique o SDM e o IDE de que o estado do aplicativo que está sendo depurado está mudando. A única diferença entre esses eventos e eventos assíncronos é que uma resposta é enviada por meio do método [ContinueFromSynchronousEvent.](../../extensibility/debugger/reference/idebugengine2-continuefromsynchronousevent.md)

   O envio de um evento síncrono é útil se você precisar do seu DE para continuar o processamento após o IDE receber e processar o evento.

- Eventos de parada síncrona ou eventos de parada

   Notifique o SDM e o IDE de que o aplicativo que está sendo depurado parou de executar o código. Quando você envia um evento de parada por meio do método [Evento,](../../extensibility/debugger/reference/idebugeventcallback2-event.md)o parâmetro [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) é necessário. Os eventos de interrupção são continuados por uma chamada para um dos seguintes métodos:

  - [Executar](../../extensibility/debugger/reference/idebugprogram2-execute.md)

  - [Etapa](../../extensibility/debugger/reference/idebugprogram2-step.md)

  - [Continuar](../../extensibility/debugger/reference/idebugprogram2-continue.md)

    As interfaces [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) são exemplos de eventos de parada.

  > [!NOTE]
  > Eventos de parada assíncrona não são suportados. É um erro enviar um evento de parada assíncrona.

## <a name="discussion"></a>Discussão
 A implementação real dos eventos depende do projeto do seu DE. O tipo de evento enviado é determinado por seus atributos, que são definidos quando você projeta o DE. Por exemplo, um DE pode enviar um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) como um evento assíncrono, enquanto outro pode enviá-lo como um evento de parada.

 A tabela a seguir especifica quais parâmetros de programa e de rosca são necessários para quais eventos, bem como tipos de eventos. Qualquer evento pode ser síncrono. Nenhum evento precisa ser síncrono.

> [!NOTE]
> A interface [IDebugEngine2](../../extensibility/debugger/reference/idebugengine2.md) é necessária para todos os eventos.

|Evento|IDebugProgram2|IDebugThread2|Eventos de interrupção|
|-----------|--------------------|-------------------|---------------------|
|[IDebugActivateDocumentEvent2](../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugBreakEvent2](../../extensibility/debugger/reference/idebugbreakevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugBreakpointUnboundEvent2](../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugCanStopEvent2](../../extensibility/debugger/reference/idebugcanstopevent2.md)|Obrigatório|Obrigatório|Não|
|[IDebugDocumentTextEvents2](../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|Não permitido|Não permitido|Não|
|[IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md)|Não permitido|Não permitido|Não|
|[IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugErrorEvent2](../../extensibility/debugger/reference/idebugerrorevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Pode ser|
|[IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Pode ser|
|[IDebugInterceptExceptionCompleteEvent2](../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugMessageEvent2](../../extensibility/debugger/reference/idebugmessageevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Pode ser|
|[IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|Obrigatório|Permitido, mas não necessário|Não|
|[IDebugOutputStringEvent2](../../extensibility/debugger/reference/idebugoutputstringevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|Obrigatório|Permitido, mas não necessário|Não|
|[IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|Obrigatório|Permitido, mas não necessário|Não|
|[IDebugPropertyCreateEvent2](../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|Obrigatório|Permitido, mas não necessário|Não|
|[IDebugPropertyDestroyEvent2](../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|Obrigatório|Permitido, mas não necessário|Não|
|[IDebugReturnValueEvent2](../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|IDebugStopCompleteEvent2|Obrigatório|Obrigatório|Sim|
|[IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|Obrigatório|Obrigatório|Sim|
|[IDebugSymbolSearchEvent2](../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|
|[IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|Obrigatório|Obrigatório|Não|
|[IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|Obrigatório|Obrigatório|Não|
|[IDebugThreadNameChangedEvent2](../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|Permitido, mas não necessário|Permitido, mas não necessário|Não|

## <a name="see-also"></a>Confira também
- [Enviando eventos](../../extensibility/debugger/sending-events.md)
