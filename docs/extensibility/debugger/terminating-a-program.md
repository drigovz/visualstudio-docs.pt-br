---
title: Terminando um Programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712517"
---
# <a name="terminating-a-program"></a>Terminando um programa
A seção a seguir descreve o término de um único programa com um segmento.

## <a name="termination-process"></a>Processo de rescisão

1. O DE envia um [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) com um [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md)válido .

2. O DE envia um [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) com um [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)válido .

   O IDE entra em modo de design. O mecanismo de depuração ou ambiente em tempo de execução chama [IDebugPortNotify2::RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) para remover o programa da porta.

## <a name="see-also"></a>Confira também
- [Chamando eventos de depurador](../../extensibility/debugger/calling-debugger-events.md)
