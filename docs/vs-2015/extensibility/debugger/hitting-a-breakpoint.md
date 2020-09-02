---
title: Atingir um ponto de interrupção | Microsoft Docs
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
ms.openlocfilehash: 0ddf7fd92ac0b2f745f9e73170de22e9724dad76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152687"
---
# <a name="hitting-a-breakpoint"></a>Atingindo um ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O seguinte descreve o processo quando o mecanismo de depuração (DE) atinge um ponto de interrupção durante a execução ou a depuração:  
  
## <a name="troubleshooting-a-hit-breakpoint"></a>Solucionando problemas de um ponto de interrupção de clique  
  
1. O DE envia uma interface [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) como um **EVENT_SYNC_STOP**.  
  
2. O SDM (Gerenciador de depuração de sessão) chama [IDebugBreakpointEvent2::: EnumBreakpoints](../../extensibility/debugger/reference/idebugbreakpointevent2-enumbreakpoints.md) para obter o ponto de interrupção que foi atingido.  
  
## <a name="see-also"></a>Consulte Também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
