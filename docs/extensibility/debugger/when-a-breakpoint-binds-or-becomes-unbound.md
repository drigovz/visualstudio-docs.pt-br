---
title: Quando um ponto de ruptura se liga ou se torna desvinculado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3253841778fe5a07e00b644423495b8ceee1a335
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712338"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando um ponto de ruptura se liga ou se torna desvinculado
Quando um ponto de ruptura não pode ser vinculado no momento em que uma chamada é feita para o [método IDebugPendingBreakpoint2::CanBind,](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) o tempo de vinculação e o tempo de criação do ponto de ruptura são diferentes.

## <a name="methods-called"></a>Métodos chamados
 O SDM (Session Debug Manager, gerenciador de depuração de sessão) chama os seguintes métodos:

1. [IDebugEngine2::CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). O DE retorna um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2::Habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2::Virtualize](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. O [método IDebugPendingBreakpoint2::Bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e retorna S_OK. O DE envia um [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. [IDebugBreakpointBoundEvent2:GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2::EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) métodos para verificar e obter os pontos de interrupção vinculados.

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)
