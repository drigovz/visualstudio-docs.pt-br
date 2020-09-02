---
title: Processos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 82718a7ceb7a18f9978840f35ca0c5fce5628e81
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153663"
---
# <a name="processes"></a>Processos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em termos da arquitetura do depurador, um **processo**:  
  
- É um contêiner para um conjunto de programas. Ele é bastante análogo a um processo do Windows, que é um contêiner para um conjunto de threads.  
  
- Pode se identificar por nome, identificador ou identificador físico.  
  
- Pode enumerar todos os programas em execução (e seus threads).  
  
- Pode se descrever, a porta em que ele está sendo executado e o computador que o contém.  
  
- Pode criar um ou mais programas, encerrar qualquer um dos programas que ele cria ou fazer com que um programa pare.  
  
- É representado por uma interface [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , que é criada quando o processo é iniciado. Um processo é iniciado pelo SDM (Gerenciador de depuração de sessão) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
  O pacote de depuração pode anexar um mecanismo DE depuração (DE) a um processo chamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Isso significa que o DE é anexado a todos os programas possíveis em execução no processo que ele pode manipular. Por exemplo, se a Common Language Runtime DE é anexada a um processo, ela é anexada somente a programas que executam código gerenciado.  
  
## <a name="see-also"></a>Consulte Também  
 [Suplementa](../../extensibility/debugger/programs.md)   
 [Threads](../../extensibility/debugger/threads.md)   
 [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)   
 [Pacote de depuração](../../extensibility/debugger/debug-package.md)   
 [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)   
 [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)   
 [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
