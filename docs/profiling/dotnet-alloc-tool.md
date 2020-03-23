---
title: Analisar o uso da memória para objetos .NET | Microsoft Docs
ms.date: 12/9/2019
ms.topic: conceptual
helpviewer_keywords:
- memory allocation, memory usage
author: Sagar-S-S
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 9518ffd618a6d82505feca33b37b5151a3a9f961
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75898465"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analisar o uso da memória usando a ferramenta .NET Object Allocation

Você pode ver quanta memória seu aplicativo está usando e quais caminhos de código alocam mais memória usando a ferramenta .NET Object Allocation.

Depois de executar a ferramenta, você pode ver os caminhos de execução da função onde os objetos estão sendo alocados para que você possa rastrear até a raiz da árvore de chamada que está ocupando a maior quantidade de memória.

## <a name="setup"></a>Instalação

1. Abra o Profiler de Desempenho **(Alt + F2)** no Visual Studio.
2.  Selecione a caixa de **seleção .NET Object Allocation Tracking.**

![Diag Hub](../profiling/media/diaghub.png "Diag Hub")

> [!NOTE]
> O projeto de inicialização é selecionado como alvo de **análise** por padrão, mas isso pode ser alterado para o processo de execução, executáveis, aplicativos em execução e aplicativos instalados abrindo o menu suspenso **do Destino** de alteração e, em seguida, selecionando entre as opções disponíveis.

   A ferramenta .NET Object Allocation não suporta executáveis no momento através do menu suspenso. Você terá que passar pelo sistema de projeto exe para usar a ferramenta. Para fazer isso, feche sua solução atual **(File** -> **Close Solution)** e, em seguida, clique **em Abrir** -> **um projeto ou solução** -> selecionar seu arquivo .exe.

![Alvo de Análise](../profiling/media/analysistarget.png "Alvo de Análise")

3. Clique no botão **Iniciar** para executar a ferramenta.

![Coleção Stop](../profiling/media/stopcollection.png "Coleção Stop")

4. Uma vez que a ferramenta comece a ser rodada, passe pelo cenário desejado em seu aplicativo e pressione **Stop Collection** ou feche seu aplicativo para ver seus dados.
5. Clique na guia **Alocação** e você deve ver uma imagem semelhante à mostrada abaixo.

![Alocação](../profiling/media/allocation.png "Alocação")

Parabéns! Agora você pode analisar a alocação de memória dos objetos.

## <a name="understand-your-data"></a>Entenda seus dados

### <a name="collection"></a>Coleção

![Coleção](../profiling/media/collection.png "Coleção")

A visão de coleta permite ver quantos objetos foram coletados durante a coleta de lixo e quantos foram retidos. Esta visualização também fornece alguns gráficos de torta para visualizar objetos coletados e sobreviventes por tipo.

- A coluna **Coletado** mostra o número de objetos que o coletor de lixo coletou.
- A **coluna Survived** mostra o número de objetos que sobreviveram após a execução do coletor de lixo.

### <a name="allocation"></a>Alocação

![Alocação Expandida](../profiling/media/allocationexpanded.png "Alocação Expandida")

A exibição de alocação permite que você veja a localização de objetos que estão alocando memória e quanta memória esses objetos estão alocando.

- A coluna **Nome** é uma lista de várias classes e estruturas que estão ocupando a memória. Cada item dentro da coluna é um nó que pode ser expandido se houver itens dentro dessa categoria ocupando a memória. (Somente**visualização de alocação)**
- A coluna **Total (Alocações)** mostra o número de objetos dentro de um determinado tipo de alocação que estão ocupando a memória. **(Alocação,** **árvore de chamada**e exibição de **funções)**
- A coluna **Auto (Alocações)** mostra o número de objetos dentro de um item individual que está ocupando a memória. **(Alocação,** **árvore de chamada**e exibição de **funções)**
- Todas as três colunas são classificadas. No caso da coluna **Nome,** os itens são ordenados alfabeticamente (para a frente ou para trás). Para **Total** e **Self (Alocações),** você pode classificar numericamente (cada vez mais ou diminuindo).
- As **colunas Tamanho Total (Bytes)** e **Tamanho Próprio (Bytes)** não estão ontadas por padrão. Para habilitá-las, clique com o botão direito do mouse nas colunas **Nome,** **Total** ou **Self (Alocações)** e, em seguida, clique nas opções **Tamanho Total** e **Tamanho próprio** para adicioná-las ao gráfico. As duas colunas são semelhantes a **Total (Alocações)** e **Self (Alocações),** exceto que, em vez de mostrar o número de objetos ocupando a memória, eles mostram a quantidade total de memória em bytes que esses objetos estão ocupando. [Somente visualização de alocação]

### <a name="call-tree"></a>Chamada árvore

![Chamada árvore](../profiling/media/calltree.png "Chamada árvore")

A **exibição Árvore de** chamada permite que você veja os caminhos de execução da função que contêm objetos alocando muita memória.

- A coluna **Nome da função** mostra o processo ou o nome da função que contém objetos que alocam memória com base no nível do nó que você está inspecionando.
- As colunas **Total** e **Self (Alocações)** mostram as mesmas informações da **exibição Alocação.**
- A coluna **Nome do Módulo** mostra o módulo que contém a função ou processo que está chamando.

![Caminho Quente](../profiling/media/hotpath.png "Afunilamento")

- O botão **Expandir caminho quente** destaca uma via de execução de função que contém um monte de objetos que estão alocando memória. O algoritmo começa em um nó de interesse selecionado pelo usuário e destaca o caminho da maioria das alocações, orientando um usuário em sua investigação.
- O botão **Mostrar caminho quente** alterna ou desliga os ícones de chama que indicam quais nós fazem parte do Caminho **Quente**.

### <a name="functions"></a>Funções

![Funções](../profiling/media/functions.png "Funções")

A **exibição de funções** mostra processos, módulos e funções que estão alocando memória.

- A coluna **Nome** mostra os processos como os nós de nível mais alto. Abaixo os processos são módulos, e em módulos estão funções.
- As colunas **Total** e **Self (Alocações)** mostram as mesmas informações da **exibição Alocação.**

As **exibições Alocações,** **Árvore de Chamada**e **Funções** contêm as opções **Show Just My Code,** **Show Native Code**e **Search:**

![Barra de filtro](../profiling/media/filterbar.png "Barra de filtro")

- **O Show Just My Code** colapsa sistemas, frameworks e outros códigos não-usuários e em quadros **[Código Externo]** para que o código do usuário possa ser focado. Para obter mais informações, consulte [Debug código de usuário com Just My Code](../debugger/just-my-code.md).
- **Mostrar Código Nativo** mostra código nativo dentro do destino de análise, incluindo código não-usuário, se selecionado.
- A **caixa Filtro** permite filtrar a coluna **Nome** ou **Função** com base no parâmetro fornecido. Basta digitar o campo e a tabela deve filtrar para baixo para mostrar apenas os tipos que contêm a seqüência fornecida.
