---
title: Erros de ponto de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoints, errors
- debugging [Debugging SDK], breakpoint errors
- errors [Debugging SDK]
ms.assetid: 79221c6b-a924-4c8e-a778-e312e4e0c0c8
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e98dc5e4645ac67ecdf5ebb06ecf0f31510202e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147986"
---
# <a name="breakpoint-errors"></a>Erros de ponto de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O seguinte descreve o processo quando um ponto de interrupção tenta se associar ao código, mas falha:  
  
## <a name="troubleshooting-a-breakpoint-error"></a>Solucionando problemas de erro de ponto de interrupção  
  
1. O mecanismo de depuração (DE) envia um [IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) para o SDM (Gerenciador de depuração de sessão).  
  
2. O SDM chama [IDebugBreakpointErrorEvent2:: GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md) (IDebugErrorBreakpoint2 * * `ppErrorBP` ) para obter o ponto de interrupção de erro.  
  
3. O SDM chama [IDebugErrorBreakpoint2:: GetPendingBreakpoint](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getpendingbreakpoint.md) para obter o ponto de interrupção pendente do qual o ponto de interrupção de erro foi originado.  
  
4. O SDM chama [IDebugErrorBreakpoint2:: GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) para obter o motivo pelo qual o ponto de interrupção de erro falhou ao associar.  
  
## <a name="see-also"></a>Consulte Também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
