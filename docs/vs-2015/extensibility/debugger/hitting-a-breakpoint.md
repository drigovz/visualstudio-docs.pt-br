---
title: Atingindo um ponto de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], hitting breakpoints
- breakpoints, hitting
ms.assetid: a77816e3-b15b-46a0-90cd-be7242e4d6c9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5ae077b8ccb4ce41f94fbc5e11bfff1f16c826c0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924941"
---
# <a name="hitting-a-breakpoint"></a>Atingindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O exemplo a seguir descreve o processo quando o mecanismo de depuração (DES) atinge um ponto de interrupção durante a execução ou passo a passo:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solução de problemas de um ponto de interrupção de ocorrência  
  
1.  O envia DE um [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface como um **EVENT_SYNC_STOP**.  
  
2.  O Gerenciador de sessão de depuração (SDM) chama [IDebugBreakpointEvent2:::EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter o ponto de interrupção foi atingido.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
