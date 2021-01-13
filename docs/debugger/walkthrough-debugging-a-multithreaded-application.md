---
title: Exibir threads no depurador | Microsoft Docs
description: Use threads para examinar e controlar threads. Você pode agrupar, classificar, sinalizar, congelar, descongelar e Pesquisar threads, selecionar colunas e exibir pilhas de chamadas.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.threads
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- threading [Visual Studio], debugging
- Thread.Name property
- debugger, Threads window
- SetThreadName function
- Threads window
- '@TIB'
- debugging [Visual Studio], threads
ms.assetid: 590ffd57-0556-43d8-8962-ee27e5b2b7d7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b02d980292eaed40c7c1598c772b52f695bf23e2
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98149697"
---
# <a name="view-threads-in-the-visual-studio-debugger-by-using-the-threads-window-c-visual-basic-c"></a>Exibir threads no depurador do Visual Studio usando a janela threads (C#, Visual Basic, C++)
Na janela **threads** , você pode examinar e trabalhar com threads no aplicativo que está depurando. Para obter orientações passo a passo sobre como usar a janela **threads** , consulte [passo a passos: depurar usando a janela threads](../debugger/how-to-use-the-threads-window.md).

## <a name="use-the-threads-window"></a>Usar a janela Threads
 A janela **threads** contém uma tabela em que cada linha descreve um thread separado em seu aplicativo. Por padrão, a tabela lista todos os threads em seu aplicativo, mas você pode filtrar a lista para mostrar apenas os threads do seu interesse. Cada coluna descreve um tipo diferente de informações. Você também pode ocultar algumas colunas. Se você exibir todas as colunas, as seguintes colunas serão exibidas da esquerda para a direita:

- **Sinalizador**: nessa coluna sem rótulo, você pode marcar um thread para o qual deseja pagar atenção especial. Para obter informações sobre como sinalizar um thread, consulte [como: sinalizador não sinalizar threads](../debugger/how-to-flag-and-unflag-threads.md).

- **O thread atual**: nesta coluna sem nome, uma seta amarela indica que o thread atual. Um contorno de seta indica o contexto do depurador atual para um thread não atual.

- **ID**: exibe o número de identificação de cada thread.

- **ID gerenciada**: exibe os números de identificação gerenciados para threads gerenciados.

- **Categoria**: exibe a categoria de threads como threads de interface do usuário, manipuladores de chamada de procedimento remoto ou threads de trabalho. Uma categoria especial identifica o thread principal do aplicativo.

- **Nome**: identifica cada thread por nome, se tiver um, ou como \<No Name> .

- **Local**: mostra onde o thread está em execução. Você pode expandir este local para mostrar a pilha de chamadas inteira para o thread.

- **Prioridade**: uma coluna avançada (ocultada por padrão) que exibe a prioridade ou precedência que o sistema atribuiu a cada thread.

- **Máscara de afinidade**: uma coluna avançada (ocultada por padrão) que mostra a máscara de afinidade do processador para cada thread. Em um sistema com vários processadores, a máscara de afinidade determina quais processadores em qual thread pode ser executado.

- **Contagem suspensa**: uma coluna avançada (ocultada por padrão) que exibe a contagem suspensa. Esta contagem determina se um thread pode ser executado. Para obter mais informações sobre contagens suspensas, consulte [congelar e descongelar Threads](#freeze-and-thaw-threads).

- **Nome do processo**: uma coluna avançada (ocultada por padrão) que exibe o processo ao qual cada thread pertence. Os dados nessa coluna podem ser úteis quando você estiver Depurando muitos processos.

- **ID do processo**: ID de uma coluna avançada (oculta por padrão) que exibe o processo ao qual pertence a cada thread.

- **Qualificador de transporte**: uma coluna avançada (ocultada por padrão) que identifica exclusivamente o computador ao qual o depurador está conectado.

### <a name="to-display-the-threads-window-in-break-mode-or-run-mode"></a>Para exibir a janela de threads no modo de interrupção ou no modo de execução

- Enquanto o Visual Studio estiver no modo de depuração, selecione o menu **depurar** , aponte para **Windows** e, em seguida, selecione **threads**.

### <a name="to-display-or-hide-a-column"></a>Para exibir ou ocultar uma coluna

- Na barra de ferramentas na parte superior da janela **threads** , selecione **colunas**. Em seguida, selecione ou limpe o nome da coluna que você deseja exibir ou ocultar.

## <a name="display-flagged-threads"></a>Exibir threads sinalizados
 Você pode sinalizar um thread ao qual deseja dar atenção especial marcando-o com um ícone na janela **Threads**. Para obter mais informações, consulte [como: sinalizar e desmarcar threads](../debugger/how-to-flag-and-unflag-threads.md). Na janela **threads** , você pode optar por exibir todos os threads ou apenas os threads sinalizados.

### <a name="to-display-only-flagged-threads"></a>Para exibir somente threads sinalizados

- Escolha **Mostrar threads sinalizados somente** na barra de ferramentas na parte superior da janela **threads** . (Se ele estiver esmaecido, você precisará sinalizar alguns threads primeiro.)

## <a name="freeze-and-thaw-threads"></a>Congelar e descongelar Threads
 Quando você congela um thread, o sistema não inicia a execução do thread, mesmo que os recursos estejam disponíveis.

 No código nativo, você pode suspender ou retomar threads chamando as funções do Windows `SuspendThread` e `ResumeThread` . Ou então, chame as funções do MFC [CWinThread:: SuspendThread](/cpp/mfc/reference/CWinThread-class#suspendthread) e [CWinThread:: ResumeThread](/cpp/mfc/reference/CWinThread-class#resumethread). Se você chamar `SuspendThread` ou `ResumeThread` , a *contagem suspensa* mostrada na janela **threads** será alterada. A contagem suspensa não será alterada se você congelar ou descongelar um thread nativo. Um thread não pode ser executado em código nativo, a menos que seja descongelado e tenha uma contagem suspensa de zero.

 No código gerenciado, a contagem suspensa é alterada quando você congela ou descongela um thread. Se você congelar um thread no código gerenciado, sua contagem suspensa será 1. Quando você congela um thread no código nativo, sua contagem suspensa é 0, a menos que você tenha usado a `SuspendThread` chamada.

> [!NOTE]
> Quando você depura uma chamada de código nativo para o código gerenciado, o código gerenciado é executado no mesmo thread físico que o código nativo que o chamou. Suspender ou congelar o thread nativo também congela o código gerenciado.

### <a name="to-freeze-or-thaw-execution-of-a-thread"></a>Para congelar ou descongelar a execução de um thread

- Na barra de ferramentas na parte superior da janela **threads** , selecione **congelar threads** ou **descongelar Threads**.

     Essa ação afeta somente os threads que estão selecionados na janela **Threads**.

### <a name="switch-to-another-thread"></a>Alternar para outro thread

Uma seta amarela indica o thread atual (e o local do ponteiro de execução). Uma seta verde com uma cauda indica que um thread não atual tem o contexto do depurador atual.

#### <a name="to-switch-to-another-thread"></a>Para alternar para outro thread

- Siga uma das seguintes etapas:

  - Clique duas vezes em qualquer thread.

  - Clique com o botão direito do mouse em um thread e selecione **alternar para thread**.

## <a name="group-and-sort-threads"></a>Agrupar e classificar threads
 Quando você agrupa threads, um título aparece na tabela para cada grupo. O título contém uma descrição do grupo, como **Thread de Trabalho** ou **Threads Sem Sinalização** e um controle de árvore. Os threads de membro de cada grupo aparecem no cabeçalho do grupo. Se você quiser ocultar os threads de membro para um grupo, use o controle de árvore para recolher o grupo.

 Como o agrupamento tem precedência sobre a classificação, você poderá agrupar threads por categoria, por exemplo, e, em seguida, classificá-los por ID dentro de cada categoria.

### <a name="to-sort-threads"></a>Para classificar threads

1. Na barra de ferramentas na parte superior da janela **threads** , selecione o botão na parte superior de qualquer coluna.

     Os threads agora são classificados pelos valores nessa coluna.

2. Se você quiser inverter a ordem de classificação, selecione o mesmo botão novamente.

     Os threads que apareceram na parte superior da lista agora aparecem na parte inferior.

### <a name="to-group-threads"></a>Para agrupar threads

- Na barra de ferramentas da janela **threads** , selecione a lista **Agrupar por** e, em seguida, selecione os critérios pelos quais você deseja agrupar threads.

### <a name="to-sort-threads-within-groups"></a>Para classificar threads dentro de grupos

1. Na barra de ferramentas na parte superior da janela **threads** , selecione a lista **Agrupar por** e, em seguida, selecione os critérios pelos quais você deseja agrupar threads.

2. Na janela **threads** , selecione o botão na parte superior de qualquer coluna.

     Os threads agora são classificados pelos valores nessa coluna.

### <a name="to-expand-or-collapse-all-groups"></a>Para expandir ou recolher todos os grupos

- Na barra de ferramentas na parte superior da janela **threads** , selecione **expandir grupos** ou **recolher grupos**.

## <a name="search-for-specific-threads"></a>Pesquisar threads específicos
 Você pode pesquisar por threads que correspondam a uma cadeia de caracteres especificada na janela **threads** . Quando você procura por threads, a janela exibe todos os threads que correspondem à cadeia de caracteres de pesquisa em qualquer coluna. Essas informações incluem o local do thread que aparece na parte superior da pilha de chamadas na coluna **Local**. Por padrão, a pilha de chamadas completa não é pesquisada.

### <a name="to-search-for-specific-threads"></a>Para pesquisar threads específicos

1. Na barra de ferramentas na parte superior da janela **Threads**, vá para a caixa **Pesquisar** e:

     - Insira uma cadeia de caracteres de pesquisa e pressione **Enter**.

     \- ou –

     - Selecione a lista suspensa ao lado da caixa de **pesquisa** e selecione uma cadeia de caracteres de pesquisa de uma pesquisa anterior.

2. (Opcional) Para incluir a pilha de chamadas inteira na pesquisa, selecione **Pesquisar Pilha de Chamadas**.

## <a name="display-thread-call-stacks-and-switch-between-frames"></a>Exibir pilhas de chamadas de thread e alternar entre os quadros
Em um programa de vários threads, cada thread tem sua própria pilha de chamadas. A janela **Threads** fornece um modo conveniente de exibir essas pilhas.

> [!TIP]
> Para uma representação visual da pilha de chamadas para cada thread, use a janela [pilhas paralelas](../debugger/get-started-debugging-multithreaded-apps.md) .

### <a name="to-view-the-call-stack-of-a-thread"></a>Para exibir a pilha de chamadas de um thread

- Na coluna **local** , selecione o triângulo invertido ao lado do local do thread.

     O local é expandido para mostrar a pilha de chamadas para o thread.

### <a name="to-view-or-collapse-the-call-stacks-of-all-threads"></a>Para exibir ou recolher as chamadas de pilhas de todos os threads

- Na barra de ferramentas na parte superior da janela **threads** , selecione **Expandir pilhas de chamadas** ou **recolher pilhas de chamadas**.

## <a name="see-also"></a>Confira também
- [Depurar aplicativos multi-threaded](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Introdução à depuração de aplicativos multi-threaded](../debugger/get-started-debugging-multithreaded-apps.md)
