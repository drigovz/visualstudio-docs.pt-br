---
title: Enviar eventos de inicialização após uma inicialização | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: caa9f615c6ed6f314695b195a6095d238382a4c2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967488"
---
# <a name="send-startup-events-after-a-launch"></a>Enviar eventos de inicialização após uma inicialização
Depois que o mecanismo de depuração (DES) é anexado ao programa, ele envia uma série de eventos de inicialização para a sessão de depuração.  
  
 Eventos de inicialização enviados de volta para a sessão de depuração incluem:  
  
- Um evento de criação de mecanismo.  
  
- Um evento de criação do programa.  
  
- Thread de criação e eventos de carregamento de módulo.  
  
- Evento complete uma carga, enviado quando o código é carregado e pronto para ser executado, mas antes de qualquer código é executado. 
  
  > [!NOTE]
  >  Quando esse evento é continuado, variáveis globais são inicializadas e executar rotinas de inicialização.  
  
- Possível que outros threads criação e eventos de carregamento de módulo.  
  
- Um evento de ponto de entrada, que sinaliza que o programa atingiu seu ponto de entrada principal, como **principal** ou `WinMain`. Esse evento geralmente não é enviado se o DE anexar a um programa que já está em execução.  
  
  O DE forma programática, primeiro o Gerenciador de sessão de depuração (SDM) envia uma [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) interface, que representa um evento de criação de mecanismo, seguido por um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) , que representa um evento de criação do programa.  
  
  Normalmente, esses eventos são seguidos por um ou mais [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) eventos de criação de thread e [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) eventos de carregamento de módulo.  
  
  Quando o código é carregado e pronto para ser executado, mas antes de qualquer código é executado, o DE envia o SDM uma [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) evento de conclusão de carga. Por fim, se o programa não estiver sendo executado, o DE envia um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) evento de ponto de entrada, sinalizando que o programa tiver atingido seu ponto de entrada principal e está pronto para depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Controle de execução](../../extensibility/debugger/control-of-execution.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)