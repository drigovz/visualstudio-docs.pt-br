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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083563"
---
# <a name="launching-the-debugger"></a>Iniciando o depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Iniciando o depurador requer o envio de sequência correta de métodos e eventos com seus atributos apropriados.  
  
## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos  
  
1. O Gerenciador de sessão de depuração (SDM) é chamado, escolhendo a **Debug** menu e, em seguida, escolhendo **iniciar**. Ver [inicializando um programa](../../extensibility/debugger/launching-a-program.md) para obter mais informações.  
  
2. As chamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.  
  
3. Com base no modelo de processo (DES) do mecanismo de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.  
  
     Se `S_FALSE` for retornado, o mecanismo de depuração (DES) deve ser carregado em andamento com a máquina virtual.  
  
     - ou -  
  
     Se `S_OK` for retornado, o DE deve ser carregado no processo do SDM. O SDM, em seguida, executa as seguintes tarefas:  
  
    1. Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.  
  
    2. Cria conjunta DE.  
  
    3. Chamadas [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md).  
  
4. O envia DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
5. O envia DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
6. O envia DE um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
7. O envia DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
8. O envia DE um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o SDM com um `EVENT_SYNC` atributo.  
  
## <a name="see-also"></a>Consulte também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)   
 [Inicializando um programa](../../extensibility/debugger/launching-a-program.md)
