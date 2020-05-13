---
title: Lançamento do Depurador | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], launching the debugger
- debugger [Debugging SDK], launching
ms.assetid: f24da1a1-f923-48b4-989f-18a22b581d1b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceb2f484449d1b3f8474a6586d298b057875b342
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738447"
---
# <a name="launch-the-debugger"></a>Inicie o depurador
O lançamento do depurador requer o envio da seqüência correta de métodos e eventos com seus atributos apropriados.

## <a name="sequences-of-methods-and-events"></a>Sequências de métodos e eventos

1. O gerenciador de depuração de sessão (SDM) é chamado escolhendo o menu **Debug** e, em seguida, escolhendo **Iniciar**. Para obter mais informações, consulte [Iniciar um programa](../../extensibility/debugger/launching-a-program.md).

2. O SDM chama o método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

3. Com base no modelo de processo do `IDebugProgramNodeAttach2::OnAttach` mecanismo de depuração (DE), o método retorna um dos seguintes métodos, que determina o que acontece a seguir.

     Se `S_FALSE` retornar, o motor de depuração (DE) deve ser carregado no processo da máquina virtual.

     -ou-

     Se `S_OK` retornar, o DE deve ser carregado em processo do SDM. Em seguida, o SDM executa as seguintes tarefas:

    1. Chama [getEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações do mecanismo do DE.

    2. Co-cria o DE.

    3. Anexação [de chamadas](../../extensibility/debugger/reference/idebugengine2-attach.md).

4. O DE envia um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para `EVENT_SYNC` o SDM com um atributo.

5. O DE envia um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para `EVENT_SYNC` o SDM com um atributo.

6. O DE envia um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para `EVENT_SYNC` o SDM com um atributo.

7. O DE envia um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para `EVENT_SYNC` o SDM com um atributo.

8. O DE envia um [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para `EVENT_SYNC` o SDM com um atributo.

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)
- [Lançamento de um programa](../../extensibility/debugger/launching-a-program.md)
