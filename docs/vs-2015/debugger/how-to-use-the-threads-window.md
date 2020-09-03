---
title: 'Como: usar a janela threads | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: adfbe002-3d7b-42a9-b42a-5ac0903dfc25
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: da41524fcb231ea399dbbd2a2904afd935e5c4f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67824251"
---
# <a name="how-to-use-the-threads-window"></a>Como usar a janela Threads
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na janela **threads** , você pode examinar e trabalhar com threads no aplicativo que você está depurando.  
  
 A janela **threads** contém uma tabela em que cada linha representa um thread em seu aplicativo. Por padrão, a tabela lista todos os threads em seu aplicativo, mas você pode filtrar a lista para mostrar apenas os threads do seu interesse. Cada coluna contém um tipo diferente de informação. Você também pode ocultar algumas colunas. Se você exibir todas as colunas, as seguintes informações são exibidas, da esquerda para a direita:  
  
- A coluna do sinalizador, em que você pode marcar um thread para o qual você deseja prestar atenção especial. Para obter informações sobre como sinalizar um thread, consulte [como: sinalizar e remover o sinalizador de threads](../debugger/how-to-flag-and-unflag-threads.md).  
  
- A coluna thread ativo, em que uma seta amarela indica um thread ativo. Um contorno de uma seta indica o thread onde a execução interrompe no depurador.  
  
- A coluna de **ID** , que contém o número de identificação de cada thread.  
  
- A coluna de **ID gerenciada** , que contém os números de identificação gerenciada para threads gerenciados.  
  
- A coluna **Category** , que categoriza os threads como threads de interface do usuário, manipuladores de chamada de procedimento remoto ou threads de trabalho. Uma categoria especial identifica o thread principal do aplicativo.  
  
- A coluna **Name** , que identifica cada thread por nome, se tiver um, ou como \<No Name> .  
  
- A coluna **Location** , que mostra onde o thread está em execução. Você pode expandir este local para mostrar a pilha de chamadas inteira para o thread.  
  
- A coluna **Priority** , que contém a prioridade ou a precedência que o sistema atribuiu a cada thread.  
  
- A coluna de **máscara de afinidade** , que é uma coluna avançada que geralmente é oculta. Esta coluna mostra a máscara de afinidade do processador para cada thread. Em um sistema com vários processadores, a máscara de afinidade determina quais processadores em qual thread pode ser executado.  
  
- A coluna de **contagem suspensa** , que contém a contagem suspensa. Esta contagem determina se um thread pode ser executado. Para obter uma explicação de contagem suspensa, consulte “Congelando e descongelando threads” posteriormente neste tópico.  
  
- A coluna **process name** , que contém o processo ao qual cada thread pertence. Esta coluna pode ser útil quando você estiver depurando vários processos, mas geralmente está oculta.  
  
### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para exibir a janela de threads no modo de interrupção ou no modo de execução  
  
- No menu **depurar** , aponte para **Windows**e clique em **threads**.  
  
### <a name="to-display-or-hide-a-column"></a>Para exibir ou ocultar uma coluna  
  
- Na barra de ferramentas na parte superior da janela **threads** , clique em **colunas**e, em seguida, selecione ou limpe o nome da coluna que você deseja exibir ou ocultar.  
  
### <a name="to-switch-the-active-thread"></a>Para alternar o thread ativo  
  
- Execute uma das seguintes etapas:  
  
  - Clique duas vezes em qualquer thread.  

  - Clique com o botão direito do mouse em um thread e clique em **alternar para thread**.  

    A seta amarela é exibida ao lado do novo thread ativo. O contorno cinza de uma seta identifica o thread onde a execução interrompe no depurador.  
  
## <a name="grouping-and-sorting-threads"></a>Agrupando e classificando threads  
 Quando você agrupa threads, um título aparece na tabela para cada grupo. O título contém uma descrição do grupo, como “Thread de trabalho” ou “Threads sem sinalização” e um controle de árvore. Os threads de membro de cada grupo aparecem no cabeçalho do grupo. Se você quiser ocultar os threads de membro para um grupo, poderá usar o controle de árvore para recolher o grupo.  
  
 Como o agrupamento tem precedência sobre a classificação, você poderá agrupar threads por categoria, por exemplo, e, em seguida, classificá-los por ID dentro de cada categoria.  
  
#### <a name="to-sort-threads"></a>Para classificar threads  
  
1. Na barra de ferramentas na parte superior da janela **threads** , clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
2. Se você quiser inverter a ordem de classificação, clique no mesmo botão novamente.  
  
     Os threads que apareceram na parte superior da lista agora aparecem na parte inferior.  
  
#### <a name="to-group-threads"></a>Para agrupar threads  
  
- Na barra de ferramentas da janela **threads** , clique na lista **Agrupar por** e, em seguida, clique nos critérios pelos quais você deseja agrupar threads.  
  
#### <a name="to-sort-threads-within-groups"></a>Para classificar threads dentro de grupos  
  
1. Na barra de ferramentas na parte superior da janela **threads** , clique na lista **Agrupar por** e clique nos critérios pelos quais você deseja agrupar threads.  
  
2. Na janela **threads** , clique no botão na parte superior de qualquer coluna.  
  
     Os threads agora são classificados pelos valores nessa coluna.  
  
#### <a name="to-expand-or-collapse-all-groups"></a>Para expandir ou recolher todos os grupos  
  
- Na barra de ferramentas na parte superior da janela **threads** , clique em **expandir grupos** ou **recolher grupos**.  
  
## <a name="searching-for-specific-threads"></a>Pesquisando threads específicos  
 No [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], você pode procurar threads que correspondem a uma cadeia de caracteres especificada. Quando você procura threads na janela **threads** , a janela exibe todos os threads que correspondem à cadeia de caracteres de pesquisa em qualquer coluna. Essas informações incluem o local do thread que aparece na parte superior da pilha de chamadas na coluna **local** . Por padrão, no entanto, a pilha de chamadas inteira não é pesquisada.  
  
#### <a name="to-search-for-specific-threads"></a>Para pesquisar threads específicos  
  
- Na barra de ferramentas na parte superior da janela **Threads**, vá para a caixa **Pesquisar** e:  
  
  - Digite uma cadeia de caracteres de pesquisa e pressione ENTER.  

    \- ou –  

  - Clique na lista suspensa ao lado da caixa de **pesquisa** e selecione uma cadeia de caracteres de pesquisa de uma pesquisa anterior.  
  
- (Opcional) Para incluir a pilha de chamadas inteira na pesquisa, selecione **Pesquisar Pilha de Chamadas**.  
  
## <a name="freezing-and-thawing-threads"></a>Congelando e descongelando threads  
 Quando você congela um thread, o sistema não iniciará a execução do thread mesmo se os recursos estiverem disponíveis.  
  
 No código nativo, você pode suspender ou retomar threads chamando as funções do Windows `SuspendThread` e `ResumeThread` ou as funções do MFC [CWinThread:: SuspendThread](https://msdn.microsoft.com/library/57189c7e-fd71-42e5-bc4b-3de7cd373d28) e [CWinThread:: ResumeThread](https://msdn.microsoft.com/library/d6f97a2f-5c9f-4ee1-b978-d74938784db5). Se você chamar `SuspendThread` ou `ResumeThread` , alterar a *contagem suspensa*, que aparece na janela **threads** . Porém, se você congelar ou descongelar um thread nativo, não alterará a contagem suspensa. No código nativo, um thread não pode ser executado a menos que seja descongelado e tenha uma contagem suspensa de zero.  
  
 No código gerenciado, congelar ou descongelar um thread altera a contagem suspensa. No código gerenciado, um thread congelado tem uma contagem suspensa de 1. No código nativo, um thread congelado tem uma contagem suspensa de 0 a menos que o thread tenha sido suspenso por uma chamada `SuspendThread`.  
  
> [!NOTE]
> Quando você depura uma chamada de código nativo para o código gerenciado, o código gerenciado é executado no mesmo thread físico que o código nativo que o chamou. Suspender ou congelar o thread nativo também congela o código gerenciado.  
  
#### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para congelar ou descongelar a execução de um thread  
  
- Na barra de ferramentas na parte superior da janela **threads** , clique em **congelar threads** ou **descongelar Threads**.  
  
     Essa ação afeta somente os threads que estão selecionados na janela **Threads**.  
  
## <a name="displaying-flagged-threads"></a>Exibindo threads sinalizados  
 Você pode sinalizar um thread ao qual deseja dar atenção especial marcando-o com um ícone na janela **Threads**. Para obter mais informações, consulte [como: sinalizar e desmarcar threads](../debugger/how-to-flag-and-unflag-threads.md). Na janela Threads, você pode optar por exibir todos os threads ou apenas os threads sinalizados.  
  
#### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados  
  
- Escolha o botão sinalizador no canto superior esquerdo da janela **threads** .  
  
## <a name="displaying-thread-call-stacks-and-switching-between-frames"></a>Exibindo pilhas de chamadas de threads e alternando entre quadros  
 Em um programa de vários threads, cada thread tem sua própria pilha de chamadas. A janela **Threads** fornece um modo conveniente de exibir essas pilhas.  
  
#### <a name="to-view-the-call-stack-of-a-thread"></a>Para exibir a pilha de chamadas de um thread  
  
- Na coluna **local** , clique no triângulo invertido ao lado do local do thread.  
  
     O local é expandido para mostrar a pilha de chamadas para o thread.  
  
#### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para exibir ou recolher as chamadas de pilhas de todos os threads  
  
- Na barra de ferramentas na parte superior da janela **threads** , clique em **Expandir pilhas de chamadas** ou **recolher pilhas de chamadas**.  
  
## <a name="see-also"></a>Consulte Também  
 [Depurar aplicativos multissegmentados](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Passo a passo: depurando um aplicativo multi-threaded](../debugger/walkthrough-debugging-a-multithreaded-application.md)
