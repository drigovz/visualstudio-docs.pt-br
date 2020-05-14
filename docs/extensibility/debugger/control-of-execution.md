---
title: Controle de Execução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], control of execution
ms.assetid: 97071846-007e-450f-95a6-f072d0f5e61e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2d338c5470611a5eea0c6279404c4eaddebb2d0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739081"
---
# <a name="control-of-execution"></a>Controle da execução
O motor de depuração (DE) normalmente envia um dos seguintes eventos como o último evento de inicialização:

- O evento de ponto de entrada, se anexando a um programa recém-lançado

- O evento completo de carga, se anexando a um programa que já está em execução

  Ambos os eventos são eventos de interrupção, o que significa que o DE aguarda uma resposta do usuário por meio do IDE. Para obter mais informações, consulte [Modos operacionais](../../extensibility/debugger/operational-modes.md).

## <a name="stopping-event"></a>Evento de parada
 Quando um evento de parada é enviado para a sessão de depuração:

1. O programa e o segmento que contêm o ponteiro de instrução atual podem ser obtidos na interface do evento.

2. O IDE determina o arquivo e a posição do código fonte atual, que ele exibe como destacado no editor.

3. A sessão de depuração normalmente responde a este primeiro evento de parada chamando o método **Continuar** do programa.

4. O programa então é executado até encontrar uma condição de parada, como acertar um ponto de interrupção. Nesse caso, o DE envia um evento de ponto de ruptura para a sessão de depuração. O evento de ponto de interrupção é um evento de parada, e o DE novamente aguarda uma resposta do usuário.

5. Se o usuário optar por entrar, ultrapassar ou sair de uma função, o IDE solicitará que a sessão de depuração chame o método do `Step` programa. O IDE passa então a unidade de passo (instrução, declaração ou linha) e o tipo de passo (se entrar, passar ou sair da função). Quando a etapa estiver concluída, o DE envia um evento completo para a sessão de depuração, que é um evento de parada.

    -ou-

    Se o usuário optar por continuar executando a partir do ponteiro de instrução atual, o IDE solicitará que a sessão de depuração chame o método **Executar** do programa. O programa retoma a execução até encontrar a próxima condição de parada.

    -ou-

    Se a sessão de depuração for ignorar um evento de parada específico, a sessão de depuração chamará o método **Continuar** do programa. Se o programa estava entrando, sobre ou fora de uma função quando encontrou a condição de parada, então ele continua o passo.

   Programáticamente, quando o DE encontra uma condição de parada, ele envia eventos de parada como [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) ou [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) para o Gerenciador de depuração de sessão (SDM) por meio de uma interface [IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) O DE passa pelas interfaces [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) e [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md) que representam o programa e o segmento que contém o ponteiro de instrução atual. O SDM chama [iDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) para obter o quadro de pilha superior e chama [IDebugStackFrame2::GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) para obter o contexto do documento associado ao ponteiro de instrução atual. Este contexto de documento é tipicamente um nome de arquivo de código fonte, linha e número da coluna. O IDE usa-os para destacar o código-fonte que contém o ponteiro de instrução atual.

   O SDM normalmente responde a este primeiro evento de parada chamando [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). O programa então é executado até encontrar uma condição de parada, como acertar um ponto de interrupção, nesse caso, o DE envia uma [Interface IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) para o SDM. O evento de ponto de interrupção é um evento de parada, e o DE novamente aguarda uma resposta do usuário.

   Se o usuário optar por entrar, ultrapassar ou sair de uma função, o IDE solicitará ao SDM que ligue para [IDebugProgram2::Step](../../extensibility/debugger/reference/idebugprogram2-step.md). O IDE passa então o [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) (instrução, declaração ou linha) e o [STEPKIND](../../extensibility/debugger/reference/stepkind.md), ou seja, se para entrar, sobre ou fora da função. Quando a etapa estiver concluída, o DE envia uma interface [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) para o SDM, que é um evento de parada.

   Se o usuário optar por continuar executando a partir do ponteiro de instrução atual, o IDE pedirá ao SDM para chamar [IDebugProgram2::Execute](../../extensibility/debugger/reference/idebugprogram2-execute.md). O programa retoma a execução até encontrar a próxima condição de parada.

   Se o pacote de depuração for ignorar um evento de parada específico, o pacote de depuração chamará o SDM, que chama [IDebugProgram2::Continue](../../extensibility/debugger/reference/idebugprogram2-continue.md). Se o programa estava entrando, sobre ou fora de uma função quando encontrou a condição de parada, ele continua o passo. Isso implica que o programa mantém um estado de desvantagem, para que ele saiba como continuar.

   As chamadas que o `Step`SDM faz para **, Executar**e **Continuar** são assíncronas, o que significa que o SDM espera que a chamada retorne rapidamente. Se o DE enviar ao SDM um `Step`evento de parada no mesmo segmento antes , **Execute**ou **Continuar** retorna, o SDM será travado.

## <a name="see-also"></a>Confira também
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
