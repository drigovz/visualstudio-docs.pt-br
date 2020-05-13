---
title: Anexo baseado em lançamento | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4910a97350366500b56593ec0076fdf0990b6d8f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738464"
---
# <a name="launch-based-attachment"></a>Anexo baseado em lançamento
O acessório baseado em lançamento a um programa é automático. Quando o processo de hospedagem do programa é iniciado pelo SDM, o anexo baseado em lançamento segue um caminho semelhante ao do método de anexo manual. Para obter informações, consulte [Anexar ao programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>O processo de anexação
 A principal diferença é a seqüência de eventos após a chamada **Anexar,** da seguinte forma:

1. Envie um objeto de evento **IDebugCreateEvent2** para o SDM. Para obter detalhes, consulte [Enviar eventos](../../extensibility/debugger/sending-events.md).

2. Ligue `IDebugProgram2::GetProgramId` para o método na interface **IDebugProgram2** passada para o método **Anexar.**

3. Envie um objeto de evento **IDebugProgramCreateEvent2** para notificar o SDM de que o objeto **IDebugProgram2** local foi criado para representar o programa ao DE.

4. Envie um objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para notificar o SDM de que um novo segmento foi criado para o processo iniciado.

## <a name="see-also"></a>Confira também
- [Envie os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)
- [Permitir que um programa seja depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
