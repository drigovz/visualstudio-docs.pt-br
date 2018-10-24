---
title: Encerrar um programa | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e15fa5746b5cd7fae66574ec0d318cad1184cfdd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49861196"
---
# <a name="terminating-a-program"></a>Terminando um programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A seguir está uma descrição do encerramento de um único programa com um thread.  
  
## <a name="termination-process"></a>Processo de encerramento  
  
1. O envia DE um [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) com uma validade [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. O envia DE um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) com uma validade [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   O IDE entra no modo de design. O mecanismo de depuração ou o ambiente de tempo de execução chama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para remover o programa da porta.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)

