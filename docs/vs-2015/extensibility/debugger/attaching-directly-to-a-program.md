---
title: Anexando diretamente a um programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: ad2b7db8-821c-440c-ba07-c55c6a395e0f
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ab49163fc1474b541df3bc1b54d336574761baa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147990"
---
# <a name="attaching-directly-to-a-program"></a>Anexando diretamente a um programa
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os usuários que desejam depurar programas em um processo que já esteja em execução normalmente seguem este processo:  
  
1. No IDE, escolha o comando **depurar processos** no menu **ferramentas** .  
  
    A caixa de diálogo **Processos** é exibida.  
  
2. Escolha um processo e clique no botão **anexar** .  
  
    A caixa de diálogo **anexar ao processo** é exibida, listando todos os mecanismos de depuração (des) instalados no computador.  
  
3. Especifique o DEs a ser usado para depurar o processo selecionado e clique em **OK**.  
  
   O pacote de depuração inicia uma sessão de depuração e passa a lista de DEs para ela. A sessão de depuração, por sua vez, passa essa lista, juntamente com uma função de retorno de chamada, para o processo selecionado e, em seguida, solicita que o processo enumere seus programas em execução.  
  
   Programaticamente, em resposta à solicitação do usuário, o pacote de depuração instancia o SDM (Gerenciador de depuração de sessão) e passa a lista de DEs selecionado para ele. Junto com a lista, o pacote de depuração passa o SDM uma interface [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) . O pacote de depuração passa a lista de DEs para o processo selecionado chamando [IDebugProcess2:: Attach](../../extensibility/debugger/reference/idebugprocess2-attach.md). Em seguida, o SDM chama [IDebugProcess2:: EnumPrograms](../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) na porta para enumerar os programas em execução no processo.  
  
   A partir desse ponto, cada mecanismo de depuração é anexado a um programa exatamente conforme detalhado na [anexação após uma inicialização](../../extensibility/debugger/attaching-after-a-launch.md), com duas exceções.  
  
   Para eficiência, o DEs que é implementado para compartilhar um espaço de endereço com o SDM é agrupado de forma que cada um deles tenha um conjunto de programas ao qual ele será anexado. Nesse caso, [IDebugProcess2](../../extensibility/debugger/reference/idebugprocess2.md) chama [IDebugEngine2:: Attach](../../extensibility/debugger/reference/idebugengine2-attach.md) e passa a ele uma matriz de programas a serem anexados.  
  
   A segunda exceção é que os eventos de inicialização enviados por uma anexação a um programa que já está em execução normalmente não incluem o evento de ponto de entrada.  
  
## <a name="see-also"></a>Consulte Também  
 [Enviando eventos de inicialização após uma inicialização](../../extensibility/debugger/sending-startup-events-after-a-launch.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
