---
title: Quando um ponto de interrupção associa ou se torna desassociado | Microsoft Docs
description: Saiba mais sobre pontos de interrupção não associados. Quando um ponto de interrupção não pode ser associado no momento em que uma chamada é feita, a hora de ligação e a hora de criação do ponto de interrupção são diferentes.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: a48bd7ff011b6e8de6e9321a00b6bc20d54f0f0b
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995909"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando um ponto de interrupção associa ou se torna desassociado
Quando um ponto de interrupção não pode ser associado no momento em que uma chamada é feita ao método [IDebugPendingBreakpoint2:: canbind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , a hora de ligação e a hora de criação do ponto de interrupção são diferentes.

## <a name="methods-called"></a>Métodos chamados
 O SDM (Gerenciador de depuração de sessão) chama os seguintes métodos:

1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). O DE retorna um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).

2. [IDebugPendingBreakpoint2:: habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).

3. [IDebugPendingBreakpoint2:: virtualizar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).

4. O método [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e retorna S_OK. O DE envia um [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).

5. Métodos [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para verificar e obter os pontos de interrupção associados.

## <a name="see-also"></a>Confira também
- [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
