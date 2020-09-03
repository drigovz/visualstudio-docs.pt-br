---
title: Quando um ponto de interrupção associa ou se torna desassociado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], breakpoint unbound events
- breakpoint bound events
ms.assetid: 61bf00b2-8293-49d3-b919-1efb0dec9151
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1425edc2c8fc3fe8c38c133388f90b18b516b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162175"
---
# <a name="when-a-breakpoint-binds-or-becomes-unbound"></a>Quando um ponto de interrupção é associado ou se torna não associado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quando um ponto de interrupção não pode ser associado no momento em que uma chamada é feita ao método [IDebugPendingBreakpoint2:: canbind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-canbind.md) , a hora de ligação e a hora de criação do ponto de interrupção são diferentes.  
  
## <a name="methods-called"></a>Métodos chamados  
 O SDM (Gerenciador de depuração de sessão) chama os seguintes métodos:  
  
1. [IDebugEngine2:: CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md). O DE retorna um [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md).  
  
2. [IDebugPendingBreakpoint2:: habilitar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-enable.md).  
  
3. [IDebugPendingBreakpoint2:: virtualizar](../../extensibility/debugger/reference/idebugpendingbreakpoint2-virtualize.md).  
  
4. O método [IDebugPendingBreakpoint2:: bind](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) e retorna S_OK. O DE envia um [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) ou [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md).  
  
5. Métodos [IDebugBreakpointBoundEvent2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugbreakpointboundevent2-getpendingbreakpoint.md) e [IDebugBreakpointBoundEvent2:: EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md) para verificar e obter os pontos de interrupção associados.  
  
## <a name="see-also"></a>Consulte Também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
