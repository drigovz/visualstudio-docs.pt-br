---
title: Processos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], processes
ms.assetid: a6a1efdc-b243-40c8-a778-6f69f6b018be
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 392c59b90bb117dded0f528bc33a617370b091a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738238"
---
# <a name="processes"></a>Processos
Na arquitetura dedepurador, um *processo:*

- É um recipiente para um conjunto de programas. É muito análogo a um processo do Windows, que é um recipiente para um conjunto de threads.

- Pode identificar-se pelo nome, identificador ou identificador físico.

- Pode enumerar todos os programas em execução (e seus tópicos).

- Pode descrever-se, a porta em que está sendo executado, e a máquina que a contém.

- Pode criar um ou mais programas, encerrar qualquer um dos programas que ele cria ou fazer com que um programa pare.

- É representado por uma interface [IDebugProcess2,](../../extensibility/debugger/reference/idebugprocess2.md) que é criada quando o processo é iniciado. Um processo é iniciado pelo Session Debug Manager (SDM) ou [pelo LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  O pacote de depuração pode anexar um mecanismo de depuração (DE) a um processo chamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), o que significa que o DE anexa a todos os programas possíveis em execução no processo que ele pode lidar. Por exemplo, se o DE em tempo de execução de idioma comum se anexar a um processo, ele se anexará apenas a programas que estão executando código gerenciado.

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Conceitos de depurador](../../extensibility/debugger/debugger-concepts.md)
- [Pacote de depuração](../../extensibility/debugger/debug-package.md)
- [Motor de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
