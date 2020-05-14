---
title: Anexando e desprendendo a um programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
- debug engines, detaching from programs
ms.assetid: 79dcbb9b-c7f8-40fc-8a00-f37fe1934f51
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8bd6ea4b51c56a3cc42036b7bd26d34ff3a3eff
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739273"
---
# <a name="attaching-and-detaching-to-a-program"></a>Anexando e desprendendo a um programa
Anexar o depurador requer o envio da seqüência correta de métodos e eventos com os atributos apropriados.

## <a name="sequence-of-methods-and-events"></a>Sequência de métodos e eventos

1. O SDM (Session Debug Manager, gerenciador de depuração de sessão) chama o método [OnAttach.](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)

    Com base no modelo de processo do `IDebugProgramNodeAttach2::OnAttach` mecanismo de depuração (DE), o método retorna um dos seguintes métodos, que determina o que acontece a seguir.

    Se `S_FALSE` for devolvido, o motor de depuração foi anexado com sucesso ao programa. Caso contrário, o método [Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md) é chamado para concluir o processo de anexação.

    Se `S_OK` for devolvido, o DE deve ser carregado no mesmo processo que o SDM. O SDM executa as seguintes tarefas:

   1. Chama [getEngineInfo](../../extensibility/debugger/reference/idebugprogramnode2-getengineinfo.md) para obter as informações do mecanismo do DE.

   2. Co-cria o DE.

   3. Anexação [de chamadas](../../extensibility/debugger/reference/idebugengine2-attach.md).

2. O DE envia um [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para `EVENT_SYNC` o SDM com um atributo.

3. O DE envia um [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para `EVENT_SYNC` o SDM com um atributo.

4. O DE envia um [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para `EVENT_SYNC_STOP` o SDM com um atributo.

   A desvinculação de um programa é um processo simples, de duas etapas, da seguinte forma:

5. O SDM chama [Desapego](../../extensibility/debugger/reference/idebugprogram2-detach.md).

6. O DE envia um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md).

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)
