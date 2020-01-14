---
title: Analisar o uso de memória para objetos .NET | Microsoft Docs
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
ms.sourcegitcommit: aa302af53de342e75793bd05b10325939dc69b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75898465"
---
# <a name="analyze-memory-usage-using-the-net-object-allocation-tool"></a>Analisar o uso de memória usando a ferramenta de alocação de objeto .NET

Você pode ver quanto memória seu aplicativo está usando e quais caminhos de código alocam a maior parte da memória usando a ferramenta de alocação de objeto .NET.

Depois de executar a ferramenta, você pode ver os caminhos de execução da função em que os objetos estão sendo alocados para que você possa rastrear de volta para a raiz da árvore de chamada que está ocupando a maior quantidade de memória.

## <a name="setup"></a>Configuração

1. Abra o criador de perfil de desempenho (**ALT + F2)** no Visual Studio.
2.  Marque a caixa de seleção **rastreamento de alocação de objeto .net** .

![Hub de diag](../profiling/media/diaghub.png "Hub de diag")

> [!NOTE]
> O projeto de inicialização é selecionado como o **destino de análise** por padrão, mas isso pode ser alterado para o processo em execução, executáveis, aplicativos em execução e aplicativos instalados abrindo o menu suspenso **alterar destino** e, em seguida, selecionando as opções disponíveis.

   Atualmente, a ferramenta de alocação de objeto do .NET não oferece suporte a executáveis por meio do menu suspenso. Você precisará passar pelo sistema de projeto exe para usar a ferramenta. Para fazer isso, feche sua solução atual (**arquivo** -> **fechar solução**) e, em seguida, clique em **arquivo** -> **abrir um projeto ou solução** -> selecione o arquivo. exe.

![Destino da análise](../profiling/media/analysistarget.png "Destino da análise")

3. Clique no botão **Iniciar** para executar a ferramenta.

![Parar coleta](../profiling/media/stopcollection.png "Parar coleta")

4. Depois que a ferramenta começar a ser executada, percorra o cenário desejado em seu aplicativo e, em seguida, pressione **parar coleta** ou feche seu aplicativo para ver seus dados.
5. Clique na guia **alocação** e você verá uma imagem semelhante à mostrada abaixo.

![Alocação](../profiling/media/allocation.png "Alocação")

Parabéns! Agora você pode analisar a alocação de memória dos objetos.

## <a name="understand-your-data"></a>Entenda seus dados

### <a name="collection"></a>Coleção

![Coleta](../profiling/media/collection.png "Coleção")

A exibição coleção permite que você veja quantos objetos foram coletados durante a coleta de lixo e quantas foram retidas. Essa exibição também fornece alguns gráficos de pizza para visualizar objetos coletados e sobreviveram por tipo.

- A coluna **coletada** mostra o número de objetos coletados pelo coletor de lixo.
- A coluna **sobreviveram** mostra o número de objetos que sobreviveram após a execução do coletor de lixo.

### <a name="allocation"></a>Alocação

![Alocação expandida](../profiling/media/allocationexpanded.png "Alocação expandida")

A exibição alocação permite que você veja o local dos objetos que estão Alocando memória e a quantidade de memória que esses objetos estão alocando.

- A coluna **Name** é uma lista de várias classes e estruturas que estão ocupando memória. Cada item dentro da coluna é um nó que pode ser expandido se houver itens dentro dessa categoria que ocupam memória. (Somente exibição de**alocação** )
- A coluna **total (alocações)** mostra o número de objetos dentro de um tipo de alocação específico que estão ocupando memória. (Exibição de**alocação**, **árvore de chamadas**e **funções** )
- A coluna **self (alocações)** mostra o número de objetos dentro de um item individual que está ocupando memória. (Exibição de**alocação**, **árvore de chamadas**e **funções** )
- Todas as três colunas são classificável. No caso da coluna **Name** , os itens são classificados alfabeticamente (para frente ou para trás). Para o **total** e o **próprio (alocações)** , você pode classificar numericamente (cada vez ou decrescente).
- As colunas **Tamanho total (bytes)** e **autotamanho (bytes)** não estão ativadas por padrão. Para habilitá-los, clique com o botão direito do mouse nas colunas **nome**, **total** ou **auto (alocações)** e clique em **Tamanho total** e opções de **autotamanho** para adicioná-las ao gráfico. As duas colunas são semelhantes ao **total (alocações)** e à **própria (alocações)** , exceto que, em vez de mostrar o número de objetos que ocupam memória, eles mostram a quantidade total de memória em bytes que esses objetos estão ocupando. [Somente exibição de alocação]

### <a name="call-tree"></a>Árvore de chamadas

![Árvore de chamadas](../profiling/media/calltree.png "Árvore de chamadas")

O modo de exibição de **árvore de chamada** permite que você veja os caminhos de execução de função que contêm objetos que alocam muita memória.

- A coluna **nome da função** mostra o processo ou o nome da função que contém objetos que alocam memória com base no nível do nó que você está inspecionando.
- As colunas **total** e **self (alocações)** mostram as mesmas informações que o modo de exibição de **alocação** .
- A coluna **nome do módulo** mostra o módulo que contém a função ou o processo que está chamando.

![Caminho quente](../profiling/media/hotpath.png "Afunilamento")

- O botão **expandir caminho quente** realça um caminho de execução de função que contém muitos objetos que estão Alocando memória. O algoritmo começa em um nó de interesse selecionado pelo usuário e realça o caminho da maioria das alocações, orientando um usuário em sua investigação.
- O botão **Mostrar caminho quente** ativa ou desativa os ícones de chama que indicam qual nó fazem parte do **Hot Path**.

### <a name="functions"></a>{1&gt;Funções&lt;1}

![Funções](../profiling/media/functions.png "{1&gt;Funções&lt;1}")

O modo de exibição de **funções** mostra processos, módulos e funções que estão Alocando memória.

- A coluna **nome** mostra processos como os nós de nível mais alto. Os processos abaixo são módulos e, em módulos, são funções.
- As colunas **total** e **self (alocações)** mostram as mesmas informações que o modo de exibição de **alocação** .

As exibições de **alocações**, **árvore de chamadas**e **funções** contêm as opções **Mostrar apenas meu código**, **Mostrar código nativo**e **Pesquisar** :

![Barra de filtro](../profiling/media/filterbar.png "Barra de filtro")

- **Mostrar apenas meu código** recolhe sistemas, estruturas e outros códigos que não são de usuário e em quadros **[código externo]** para que o código do usuário possa se concentrar. Para obter mais informações, consulte [depurar código do usuário com apenas meu código](../debugger/just-my-code.md).
- **Mostrar código nativo** mostra o código nativo dentro do destino de análise, incluindo código que não é de usuário, se selecionado.
- A **caixa de filtro** permite filtrar a coluna **nome** ou **nome da função** com base no parâmetro fornecido. Basta digitar o campo e a tabela deve filtrar para mostrar apenas os tipos que contêm a cadeia de caracteres fornecida.
