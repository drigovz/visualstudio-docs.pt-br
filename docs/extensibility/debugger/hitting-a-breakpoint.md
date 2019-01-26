---
title: Atingindo um ponto de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0df2de67466205c9dfe3cd27b338762b80c888ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54959064"
---
# <a name="hit-a-breakpoint"></a>Atingir um ponto de interrupção
A seção a seguir descreve o processo quando o mecanismo de depuração (DES) atinge um ponto de interrupção durante a execução ou passo a passo:  
  
## <a name="troubleshoot-a-hit-breakpoint"></a>Solucionar problemas de um ponto de interrupção de ocorrência  
  
1.  O envia DE um [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface como um **EVENT_SYNC_STOP**.  
  
2.  O Gerenciador de sessão de depuração (SDM) chama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter o ponto de interrupção foi atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)