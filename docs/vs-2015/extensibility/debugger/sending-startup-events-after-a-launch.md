---
title: Enviando eventos de inicialização após uma inicialização | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838462"
---
# <a name="sending-startup-events-after-a-launch"></a>Enviado eventos de inicialização após uma inicialização
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Depois que o mecanismo de depuração (DE) é anexado ao programa, ele envia uma série de eventos de inicialização de volta para a sessão de depuração.  
  
 Os eventos de inicialização enviados de volta para a sessão de depuração incluem o seguinte:  
  
- Um evento de criação de mecanismo.  
  
- Um evento de criação de programa.  
  
- Criação de threads e eventos de carregamento de módulo.  
  
- Um evento de carregamento concluído, enviado quando o código é carregado e está pronto para ser executado, mas antes de qualquer código ser executado  
  
  > [!NOTE]
  > Quando esse evento é continuado, as variáveis globais são inicializadas e as rotinas de inicialização são executadas.  
  
- Possível criação de thread e eventos de carregamento de módulo.  
  
- Um evento de ponto de entrada, que sinaliza que o programa atingiu seu ponto de entrada principal, como **Main** ou `WinMain` . Esse evento normalmente não será enviado se o DE for anexado a um programa que já está em execução.  
  
  Programaticamente, o primeiro envia o SDM (Gerenciador de depuração de sessão) uma interface [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , que representa um evento de criação de mecanismo, seguido por um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), que representa um evento de criação de programa.  
  
  Normalmente, isso é seguido por um ou mais eventos de criação de thread [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) e eventos de carregamento de módulo [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
  Quando o código é carregado e está pronto para ser executado, mas antes de qualquer código ser executado, o DE envia o SDM um evento de carga concluída do [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) . Por fim, se o programa ainda não estiver em execução, o DE enviará um evento DE ponto de entrada [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , sinalizando que o programa atingiu seu ponto de entrada principal e está pronto para depuração.  
  
## <a name="see-also"></a>Consulte Também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
