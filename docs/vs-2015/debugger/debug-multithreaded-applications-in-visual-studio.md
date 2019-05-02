---
title: Depurar aplicativos multithread
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.gputthreads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- debugging [Visual Studio], high-performance computing
- debugging [Visual Studio], multithreaded
- multithreaded debugging
- high-performance debugging
ms.assetid: 9d175bc2-1d95-4c47-9bc3-9755af968a9c
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8315a797aec5fcedbf33df6ca96f41879b57d971
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60054294"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicativos multithread no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um thread é uma sequência de instruções para que o sistema operacional aloque tempo no processador. Cada processo que está em execução no sistema operacional consiste em pelo menos um thread. Os processos que têm mais de um thread são chamados multithread.

 Os computadores com vários processadores, processadores de vários núcleos ou processos de hyperthreading podem executar vários threads ao mesmo tempo. O processamento paralelo de vários threads pode aumentar melhorar o desempenho do programa, mas também pode tornar a depuração mais difícil porque apresenta a necessidade de manter controle de vários threads.

 Além disso, o multithreading apresenta alguns novos tipos de bugs potenciais. Geralmente, dois ou mais threads precisam acessar o mesmo recurso, mas apenas um thread pode acessar com segurança o recurso de cada vez. Alguma forma de exclusão mútua é necessário para certificar-se de que apenas um thread está acessando o recurso de cada vez. Se a exclusão mútua for executada incorretamente, pode criar uma *deadlock* condição em que nenhum thread possa executar. Deadlocks podem ser um problema particularmente difícil de depurar.

 O Visual Studio fornece um **Threads** janela, uma janela de Threads da GPU, uma janela de inspeção paralela e outros recursos que tornam a depuração de vários segmentos. A melhor maneira de aprender sobre os recursos de threads é seguindo as orientações. Confira [Passo a passo: Depurando um aplicativo multi-threaded](../debugger/walkthrough-debugging-a-multithreaded-application.md) e [passo a passo: Depurando um aplicativo C++ AMP](http://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 O Visual Studio também fornece os pontos de interrupção avançados e pontos de controle, que podem ser muito úteis quando você depura aplicativos multissegmentados. Você pode usar filtros de ponto de interrupção para incluir pontos de interrupção em threads individuais. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md)

 Depurar um aplicativo com vários thread que tenha uma interface de usuário pode ser especialmente difícil. Nesse caso, você poderá considerar a execução do aplicativo em um segundo computador e o uso da depuração remota. Para obter informações, consulte [depuração remota](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Nesta seção
 [Depurar Threads e processos](../debugger/debug-threads-and-processes.md) explica as Noções básicas de depuração de threads e processos.

 [Depurar vários processos](../debugger/debug-multiple-processes.md) explica como depurar vários processos.

 [Como: Usar a janela Threads](../debugger/how-to-use-the-threads-window.md) procedimentos úteis para depurar threads com o **Threads** janela.

 [Como: Alternar para outro Thread enquanto a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md) três maneiras para alternar o contexto de depuração para outro thread.

 [Como: Sinalizador e remover sinalização de Threads](../debugger/how-to-flag-and-unflag-threads.md) marque ou sinalize threads que você deseja dar atenção especial durante a depuração.

 [Como: Definir um nome de Thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) atribua ao thread um nome que você vê na **Threads** janela.

 [Como: Definir um nome de Thread em código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md) atribua ao thread um nome que você vê na **Threads** janela.

 [Passo a passo: Depurando um aplicativo multi-threaded](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Um tour guiado dos recursos de depuração com ênfase nos recursos para [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Como: Depurar em um Cluster de alto desempenho](../debugger/how-to-debug-on-a-high-performance-cluster.md) técnicas para depurar um aplicativo executado em um cluster de alto desempenho.

 [Dicas para Threads de depuração em código nativo](../debugger/tips-for-debugging-threads-in-native-code.md) técnicas simples que podem ser úteis para depurar threads nativos.

 [Usando a janela tarefas](../debugger/using-the-tasks-window.md) mostra uma lista de todos os objetos de tarefa gerenciado ou nativo, incluindo seu status e outras informações úteis.

 [Usando a janela Parallel Stacks](../debugger/using-the-parallel-stacks-window.md) chamada mostra as pilhas de vários threads (ou tarefas) em uma única exibição e ele também agrega os segmentos de pilha que são comuns entre os threads (ou tarefas).

 [Passo a passo: Depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) passo a passo que mostra como usar as janelas de tarefas paralelas e pilhas paralelas.

 [Como: Usar a janela Inspeção paralela](../debugger/how-to-use-the-parallel-watch-window.md) inspecionar os valores e expressões entre vários threads.

 [Como: Usar a janela de Threads da GPU](../debugger/how-to-use-the-gpu-threads-window.md) examinar e trabalhar com threads que estão em execução no GPU durante a depuração.

## <a name="related-sections"></a>Seções relacionadas

[Usando pontos de interrupção](../debugger/using-breakpoints.md)
- Use filtros de ponto de interrupção quando você deseja colocar um ponto de interrupção em um segmento individual.

- Os pontos de controle permitem que você rastreie a execução do programa sem interrupções. Isso pode ser útil para estudar problemas, como deadlocks.

  [Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) conceitos de segmentação na [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programação, incluindo o código de exemplo.

  [Multithreading em componentes](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) como usar multithreading em [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componentes.

  [Suporte de multithreading para código anterior (Visual C++)](http://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) conceitos de segmentação e código de exemplo para programadores de C++ usando o MFC.

## <a name="see-also"></a>Consulte também
 [Depurar Threads e processos](../debugger/debug-threads-and-processes.md) [depuração remota](../debugger/remote-debugging.md)
