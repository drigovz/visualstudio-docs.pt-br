---
title: Anexando diretamente a um programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9a5699ee81b8c8ae36bcf492e93467615a9e89
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739256"
---
# <a name="attach-directly-to-a-program"></a>Anexar diretamente a um programa
Os usuários que desejam depurar programas em um processo que já está sendo executado normalmente seguem esse processo:

1. No IDE, escolha o comando **Debug Processes** no menu **Ferramentas.**

    A caixa de diálogo **Processos** é exibida.

2. Escolha um processo e clique no botão **Anexar.**

    A caixa de diálogo **Anexar ao processo** é exibida, listando todos os mecanismos de depuração (DEs) instalados na máquina.

3. Especifique os DEs para usar para depurar o processo selecionado e clique em **OK**.

   O pacote de depuração inicia uma sessão de depuração e passa a lista de DEs para ele. A sessão de depuração, por sua vez, passa esta lista, juntamente com uma função de retorno de chamada, para o processo selecionado e, em seguida, pede que o processo enumeraseus programas em execução.

   Programáticamente, em resposta à solicitação do usuário, o pacote de depuração instancia o Gerenciador de depuração de sessão (SDM) e passa a lista de DEs selecionados para ele. Junto com a lista, o pacote de depuração passa ao SDM uma interface [IDebugEventCallback2.](../../extensibility/debugger/reference/idebugeventcallback2.md) O pacote de depuração passa a lista de DEs para o processo selecionado chamando [IDebugProcess2::Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Em seguida, o SDM chama [iDebugProcess2::EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porta para enumerar os programas em execução no processo.

   A partir deste ponto, cada mecanismo de depuração é anexado a um programa exatamente como detalhado em [Attaching após um lançamento,](../../extensibility/debugger/attaching-after-a-launch.md)com duas exceções.

   Para eficiência, os DEs que são implementados para compartilhar um espaço de endereço com o SDM são agrupados para que cada DE tenha um conjunto de programas aos os que será anexado. Neste caso, [o IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chama [iDebugEngine2::Anexar](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa-o a uma matriz de programas para anexar.

   A segunda exceção é que os eventos de inicialização enviados por um DE anexando a um programa que já está em execução não incluem normalmente o evento de ponto de entrada.

## <a name="see-also"></a>Confira também
- [Envio de eventos de startup após um lançamento](../../extensibility/debugger/sending-startup-events-after-a-launch.md)
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
