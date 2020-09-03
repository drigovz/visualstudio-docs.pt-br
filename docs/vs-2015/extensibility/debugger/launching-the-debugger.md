---
title: Iniciando o depurador | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e9c57079246dd52bd7fb44371999d0c3747dad40
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149122"
---
# <a name="launching-the-debugger"></a>Iniciando o depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Iniciar o depurador requer o envio da sequência correta de métodos e eventos com seus atributos adequados.  
  
## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos  
  
1. O SDM (Gerenciador de depuração de sessão) é chamado escolhendo o menu **depurar** e, em seguida, escolhendo **Iniciar**. Consulte [iniciando um programa](../../extensibility/debugger/launching-a-program.md) para obter mais informações.  
  
2. O SDM chama o método [onattach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) .  
  
3. Com base no modelo de processo do mecanismo DE depuração (DE), o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos seguintes métodos, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração (de) será carregado no processo da máquina virtual.  
  
     - ou -  
  
     Se `S_OK` for retornado, o de será carregado no processo do SDM. O SDM executa as seguintes tarefas:  
  
    1. Chama [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações do mecanismo de de.  
  
    2. Cocria o DE.  
  
    3. Chama [Attach](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4. O DE envia um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
5. O DE envia um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
6. O DE envia um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
7. O DE envia um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
8. O DE envia um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Consulte Também  
 [Chamando eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicializando um programa](../../extensibility/debugger/launching-a-program.md)
