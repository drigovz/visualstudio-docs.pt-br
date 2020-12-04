---
title: Processos | Microsoft Docs
description: Este artigo descreve a definição e a função de um processo na arquitetura do depurador no Visual Studio.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 4a707d62443004795824c8bd437c29802635cf41
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606496"
---
# <a name="processes"></a>Processos
Na arquitetura do depurador, um *processo*:

- É um contêiner para um conjunto de programas. Ele é bastante análogo a um processo do Windows, que é um contêiner para um conjunto de threads.

- Pode se identificar por nome, identificador ou identificador físico.

- Pode enumerar todos os programas em execução (e seus threads).

- Pode se descrever, a porta em que ele está sendo executado e o computador que o contém.

- Pode criar um ou mais programas, encerrar qualquer um dos programas que ele cria ou fazer com que um programa pare.

- É representado por uma interface [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) , que é criada quando o processo é iniciado. Um processo é iniciado pelo SDM (Gerenciador de depuração de sessão) ou [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

  O pacote de depuração pode anexar um mecanismo DE depuração (DE) a um processo chamando [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md), o que significa que o de é anexado a todos os programas possíveis em execução no processo que ele pode manipular. Por exemplo, se a Common Language Runtime DE é anexada a um processo, ela é anexada somente a programas que executam código gerenciado.

## <a name="see-also"></a>Confira também
- [Programas](../../extensibility/debugger/programs.md)
- [Threads](../../extensibility/debugger/threads.md)
- [Conceitos do depurador](../../extensibility/debugger/debugger-concepts.md)
- [Pacote de depuração](../../extensibility/debugger/debug-package.md)
- [Mecanismo de depuração](../../extensibility/debugger/debug-engine.md)
- [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md)
