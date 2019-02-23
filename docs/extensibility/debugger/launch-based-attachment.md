---
title: Anexo com base em Iniciar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f4a967b48f7c904ecc22d0b3ea077ae5cecd2625
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718957"
---
# <a name="launch-based-attachment"></a>Anexo de inicialização
Com base em inicialização anexo a um programa é automático. Quando o processo que hospeda o programa é iniciado pelo SDM, anexo com base em inicialização segue um caminho semelhante do método manual de anexo. Para obter informações, consulte [anexação ao programa](../../extensibility/debugger/attaching-to-the-program.md).

## <a name="the-attaching-process"></a>O processo de anexar
 A principal diferença é a sequência de eventos a seguir a **Attach** chamar, da seguinte maneira:

1.  Enviar um **IDebugEngineCreateEvent2** o objeto de evento para o SDM. Para obter detalhes, consulte [enviar eventos](../../extensibility/debugger/sending-events.md).

2.  Chame o `IDebugProgram2::GetProgramId` método na **IDebugProgram2** interface é passada para o **Attach** método.

3.  Enviar um **IDebugProgramCreateEvent2** objeto de evento para notificar o SDM que local **IDebugProgram2** objeto foi criado para representar o programa para a Alemanha.

4.  Enviar um [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) o objeto de evento para notificar o SDM que um novo thread é criado para o processo que o iniciou.

## <a name="see-also"></a>Consulte também
- [Enviar os eventos necessários](../../extensibility/debugger/sending-the-required-events.md)
- [Habilitar um programa a ser depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)