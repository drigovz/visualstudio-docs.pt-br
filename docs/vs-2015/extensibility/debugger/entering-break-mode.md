---
title: Entrando no modo de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4251779593e237713258fd54c80dcb311ce4b80
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182245"
---
# <a name="entering-break-mode"></a>Entrando no modo de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O seguinte descreve o processo que ocorre quando um ponto de interrupção é encontrado após a depuração em uma função, em execução na linha de código-fonte que tem o cursor em si ou em execução em um ponto de interrupção.  
  
## <a name="break-mode-process"></a>Processo de modo de interrupção  
  
1. O mecanismo DE depuração (DE) envia [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)ou qualquer outro evento de interrupção para fazer com que o IDE entre no modo de interrupção.  
  
2. O SDM Obtém as informações da pilha de chamadas do thread, da seguinte maneira:  
  
    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)  
  
    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)  
  
    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)  
  
    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter as informações do código-fonte  
  
    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) obter o nome do arquivo  
  
    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) para obter o intervalo de instruções  
  
    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) para obter informações de memória  
  
## <a name="see-also"></a>Consulte Também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
