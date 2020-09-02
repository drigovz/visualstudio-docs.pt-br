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
ms.openlocfilehash: 8cb43c9a32f3dfd0a6383d466f7cd283acf0ab3a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691275"
---
# <a name="debug-multithreaded-applications-in-visual-studio"></a>Depurar aplicativos multithread no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um thread é uma sequência de instruções para que o sistema operacional aloque tempo no processador. Cada processo que está em execução no sistema operacional consiste em pelo menos um thread. Os processos que têm mais de um thread são chamados multithread.

 Os computadores com vários processadores, processadores de vários núcleos ou processos de hyperthreading podem executar vários threads ao mesmo tempo. O processamento paralelo de vários threads pode aumentar melhorar o desempenho do programa, mas também pode tornar a depuração mais difícil porque apresenta a necessidade de manter controle de vários threads.

 Além disso, o multithreading apresenta alguns novos tipos de bugs potenciais. Geralmente, dois ou mais threads precisam acessar o mesmo recurso, mas apenas um thread pode acessar com segurança o recurso de cada vez. Alguma forma de exclusão mútua é necessário para certificar-se de que apenas um thread está acessando o recurso de cada vez. Se a exclusão mútua for executada incorretamente, ela poderá criar uma condição de *deadlock* em que nenhum thread possa ser executado. Deadlocks podem ser um problema particularmente difícil de depurar.

 O Visual Studio fornece uma janela **threads** , uma janela threads de GPU, uma janela inspeção paralela e outros recursos que facilitam a depuração multithread. A melhor maneira de aprender sobre os recursos de threading é fazendo as orientações. Consulte [Walkthrough: Depurando um aplicativo com vários threads](../debugger/walkthrough-debugging-a-multithreaded-application.md) e [Walkthrough: Depurando um aplicativo C++ amp](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5).

 O Visual Studio também fornece os pontos de interrupção avançados e pontos de controle, que podem ser muito úteis quando você depura aplicativos multissegmentados. Você pode usar filtros de ponto de interrupção para incluir pontos de interrupção em threads individuais. Consulte [usando pontos de interrupção](../debugger/using-breakpoints.md)

 Depurar um aplicativo com vários thread que tenha uma interface de usuário pode ser especialmente difícil. Nesse caso, você poderá considerar a execução do aplicativo em um segundo computador e o uso da depuração remota. Para obter informações, consulte [depuração remota](../debugger/remote-debugging.md).

## <a name="in-this-section"></a>Nesta seção
 [Depurar threads e processos](../debugger/debug-threads-and-processes.md) Explica os conceitos básicos de depuração de threads e processos.

 [Depurar vários processos](../debugger/debug-multiple-processes.md) Explica como depurar vários processos.

 [Como: usar a janela threads](../debugger/how-to-use-the-threads-window.md) Procedimentos úteis para depurar threads com a janela **threads** .

 [Como alternar para outro thread durante a depuração](../debugger/how-to-switch-to-another-thread-while-debugging.md) Três maneiras de alternar o contexto de depuração para outro thread.

 [Como: sinalizar e remover o sinalizador de threads](../debugger/how-to-flag-and-unflag-threads.md) Marque ou sinalize threads para os quais você deseja dar atenção especial durante a depuração.

 [Como definir um nome de thread em código nativo](../debugger/how-to-set-a-thread-name-in-native-code.md) Dê ao seu thread um nome que você exiba na janela **threads** .

 [Como: definir um nome de thread em código gerenciado](../debugger/how-to-set-a-thread-name-in-managed-code.md) Dê ao seu thread um nome que você exiba na janela **threads** .

 [Walkthrough: Depurando um aplicativo multithread](../debugger/walkthrough-debugging-a-multithreaded-application.md).
Um tour guiado dos recursos de depuração com ênfase nos recursos para [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)].

 [Como depurar em um cluster de alto desempenho](../debugger/how-to-debug-on-a-high-performance-cluster.md) Técnicas para depurar um aplicativo que é executado em um cluster de alto desempenho.

 [Dicas para depurar threads em código nativo](../debugger/tips-for-debugging-threads-in-native-code.md) Técnicas simples que podem ser úteis para depurar threads nativos.

 [Usando a janela tarefas](../debugger/using-the-tasks-window.md) Mostra uma lista de todos os objetos de tarefa gerenciados ou nativos, incluindo seu status e outras informações úteis.

 [Usando a janela pilhas paralelas](../debugger/using-the-parallel-stacks-window.md) Mostra pilhas de chamadas de vários threads (ou tarefas) em uma única exibição e também une segmentos de pilha que são comuns entre os threads (ou tarefas).

 [Walkthrough: Depurando um aplicativo paralelo](../debugger/walkthrough-debugging-a-parallel-application.md) Walkthrough que mostra como usar as janelas de tarefas paralelas e de pilhas paralelas.

 [Como: usar a janela de inspeção paralela](../debugger/how-to-use-the-parallel-watch-window.md) Inspecione valores e expressões em vários threads.

 [Como: usar a janela threads GPU](../debugger/how-to-use-the-gpu-threads-window.md) Examine e trabalhe com threads que estão em execução na GPU durante a depuração.

## <a name="related-sections"></a>Seções relacionadas

[Usando pontos de interrupção](../debugger/using-breakpoints.md)
- Use filtros de ponto de interrupção quando você deseja colocar um ponto de interrupção em um segmento individual.

- Os pontos de controle permitem que você rastreie a execução do programa sem interrupções. Isso pode ser útil para estudar problemas, como deadlocks.

  [Threading](https://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87) Conceitos de Threading em [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] programação, incluindo código de exemplo.

  [Multithreading em componentes](https://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779) Como usar multithreading em [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] componentes.

  [Suporte multithread para código mais antigo (Visual C++)](https://msdn.microsoft.com/library/24425b1f-5031-4c6b-aac7-017115a40e7c) Conceitos de threading e código de exemplo para programadores de C++ usando o MFC.

## <a name="see-also"></a>Consulte Também
 [Depurar threads e processar](../debugger/debug-threads-and-processes.md) a [depuração remota](../debugger/remote-debugging.md)
