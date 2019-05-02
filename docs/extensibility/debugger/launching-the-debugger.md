---
title: Iniciando o depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ffe0405b1e07bfb7825607e17088f0f75796197
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62889430"
---
# <a name="launch-the-debugger"></a>Iniciar o depurador
Iniciando o depurador requer o envio de sequência correta de métodos e eventos com seus atributos apropriados.

## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos

1. O Gerenciador de sessão de depuração (SDM) é chamado, escolhendo a **Debug** menu e, em seguida, escolhendo **iniciar**. Para obter mais informações, consulte [iniciar um programa](../../extensibility/debugger/launching-a-program.md).

2. As chamadas SDM [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método.

3. Com base no modelo de processo (DES) do mecanismo de depuração, o `IDebugProgramNodeAttach2::OnAttach` método retorna um dos métodos a seguir, que determina o que acontece em seguida.

     Se `S_FALSE` retorna, o mecanismo de depuração (DES) deve ser carregado em andamento com a máquina virtual.

     - ou -

     Se `S_OK` retorna, o DE deve ser carregado no processo do SDM. O SDM, em seguida, executa as seguintes tarefas:

    1. Chamadas [GetEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações de mecanismo de.

    2. Cria conjunta DE.

    3. Chamadas [anexar](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. O envia DE um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.

5. O envia DE um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.

6. O envia DE um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para o SDM com um `EVENT_SYNC` atributo.

7. O envia DE um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM com um `EVENT_SYNC` atributo.

8. O envia DE um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o SDM com um `EVENT_SYNC` atributo.

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
- [Iniciar um programa](../../extensibility/debugger/launching-a-program.md)