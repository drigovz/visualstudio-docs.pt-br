---
title: Envio dos Eventos Necessários | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], required events
ms.assetid: 08319157-43fb-44a9-9a63-50b919fe1377
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc83b47e53607fe1111ececbbf892c96f7bbb639
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713004"
---
# <a name="send-the-required-events"></a>Envie os eventos necessários
Use este procedimento para enviar eventos necessários.

## <a name="process-for-sending-required-events"></a>Processo para envio de eventos necessários
 Os seguintes eventos são necessários, nesta ordem, ao criar um mecanismo de depuração (DE) e anexá-lo a um programa:

1. Envie um objeto de evento [IDebugCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) para o SDM (Session Debug Manager, gerenciador de depuração de sessão) quando o DE for inicializado para depurar um ou mais programas em um processo.

2. Quando o programa a ser depurado for anexado, envie um objeto de evento [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md) para o SDM. Este evento pode ser um evento de parada, dependendo do design do motor.

3. Se o programa estiver conectado quando o processo for iniciado, envie um objeto de evento [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) para o SDM para notificar o IDE do novo segmento. Este evento pode ser um evento de parada, dependendo do design do motor.

4. Envie um objeto de evento [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) para o SDM quando o programa que está sendo depurado estiver concluído ou quando a anexação ao programa estiver concluída. Este evento deve ser um evento de parada.

5. Se o aplicativo a ser depurado for iniciado, envie um objeto de evento [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o SDM quando a primeira instrução de código na arquitetura de tempo de execução estiver prestes a ser executada. Este evento é sempre um evento de parada. Ao entrar na sessão de depuração, o IDE pára neste evento.

> [!NOTE]
> Muitas línguas usam inicializadores globais ou funções externas pré-compiladas (da biblioteca CRT ou _Main) no início de seu código. Se o idioma do programa que você está depurando contiver qualquer um desses tipos de elementos antes do ponto de **main** entrada `WinMain`inicial, este código será executado e o evento de ponto de entrada é enviado quando o ponto de entrada do usuário, como principal ou , é atingido.

## <a name="see-also"></a>Confira também
- [Permitindo que um programa seja depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
