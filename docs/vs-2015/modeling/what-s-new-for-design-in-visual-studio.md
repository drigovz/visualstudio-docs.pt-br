---
title: O que&#39;s novos para o design
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- what's new [VIsual Studio], architecture and modeling
- architecture [Visual Studio Ultimate], modeling
- modeling software [Visual Studio], What's New
ms.assetid: 36ab5c17-6dc0-4075-a28e-a0fa49b11260
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 84b5ed45bfa7117eec4cbaa86ad9ca4533339d62
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "59000295"
---
# <a name="whats-new-for-design-in-visual-studio-in-visual-studio-2015"></a>O que há de novo no design no Visual Studio no Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Esta versão do Visual Studio inclui os seguintes aprimoramentos para ajudá-lo a entender melhor e criar o código.

 **Mapas de código e gráficos de dependência**

 No Visual Studio Enterprise, quando você quiser entender dependências específicas em seu código, exiba-os Criando mapas de código. Assim, você pode navegar entre essas relações usando o mapa que aparece ao lado do código. Os mapas de código também podem ajudar a saber em que parte do código você está enquanto trabalha ou depura código, para que seja necessário ler menos código enquanto examina o design do código.

 Na versão final (RTM), fizemos os menus de atalho para elementos de código e links muito mais fácil de usar, agrupando comandos em seções relacionadas ao selecionar, edição, gerenciamento de grupos e alterando o layout do conteúdo do grupo. Observe também que os projetos de teste são exibidos em um estilo diferente de outros projetos e que atualizamos os ícones de elementos no mapa para versões mais adequadas.

 ![Mostrar itens selecionados em um novo mapa de códigos](../ide/media/codemapsshowonnewmap.png "CodeMapsShowOnNewMap")

 Outros aprimoramentos incluem:

- **Diagramas de cima para baixo melhorados**. Para soluções médias a grandes do Visual Studio, agora você pode usar um menu de arquitetura simplificado para obter mapas de códigos mais eficientes para sua solução. Os assemblies da solução são agrupados pelas pastas da solução para que você possa vê-los no contexto e usufruir do esforço que empregou para estruturar a solução. Você verá imediatamente referências de projeto e assembly e, em seguida, aparecerão os tipos de link. Além disso, os assemblies que estiverem externos à solução serão agrupados de uma maneira mais compacta.

- **Os projetos de teste têm estilo diferente e podem ser filtrados**. Você pode agora mais fácil e rapidamente identificar os projetos de teste no mapa porque eles têm estilos diferentes. Eles também podem ser filtrados para que você possa se concentrar no código de trabalho do aplicativo.

- **Links de dependência externa simplificados**. Os links de dependência não representam mais a herança de System.Object, System.ValueType, System.Enum e System.Delegate, o que facilita a visualização das dependências externas no mapa de códigos.

- **O 'Aprofundamento nos links de dependência' leva os filtros em consideração**. Você obtém um diagrama simples e útil quando o expande para compreender as contribuições a um link de dependência. O diagrama é menos desorganizado e leva em consideração as opções de filtragem de link que você selecionou.

- **Os elementos de código são adicionados a um mapa de código com seus contextos**. Como os diagramas agora aparecem com contexto (até o assembly e a pasta de solução, que podem ser filtrados, se necessário), você pode obter diagramas mais eficientes ao arrastar e soltar elementos de código do Gerenciador de Soluções, do Modo de Exibição de Classe e do Pesquisador de Objetos ou ao solicitar elementos no Gerenciador de Soluções e escolher Exibir no Mapa de Códigos.

- **Obtenha mapas de código reativos mais rapidamente**. As operações de arrastar e soltar produzem um resultado imediato, e os links entre os nós são criados com muito mais rapidez, sem afetar as operações posteriores iniciadas pelo usuário, como expandir um nó ou solicitar mais nós. Quando você cria mapas de código sem compilar a solução, todos os casos de canto, como quando os assemblies não são compilados, são agora compilados.

- **Ignorar a recompilação de sua solução.** Fornece um melhor desempenho durante a criação e edição de diagramas.

- **Filtrar nós e grupos de elemento de código**. Você pode organizar rapidamente seus mapas ao exibir ou ocultar elementos de código com base na categoria e ao agrupar elementos de código por pastas de solução, assemblies, namespaces, pastas de projeto e tipos.

- **Filtre relações para tornar os diagramas mais fáceis de ler**. Agora, a filtragem de links também se aplica a links de grupos cruzados, o que torna o trabalho com a janela de filtros menos intrusivo do que era nas versões anteriores.

- **Criar diagramas do Modo de Exibição de Classe e do Pesquisador de Objetos**. Arraste e solte arquivos e assemblies em um mapa novo ou existente nas janelas Modo de Exibição de Classe e Pesquisador de Objetos.

  Ver [mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md).

  **Outras alterações de design e modelagem nesta versão:**

- **Diagramas de camada**. Atualize esses diagramas usando o modo de exibição de classe e Pesquisador de objetos. Para atender aos requisitos de design de software, use diagramas de camada para descrever as dependências desejadas para seu software. Mantenha o código consistente com esse design, localizando o código que não atende a essas restrições e validando códigos futuros com essa linha de base.

- **Diagramas de UML**. Não é mais possível criar diagramas de classe UML e diagramas de sequência por meio do código. Mas ainda é possível criar esses diagramas usando novos elementos UML.

- **Architecture Explorer**. Não é mais possível usar o Architecture Explorer para criar diagramas. Mas ainda é possível usar o Gerenciador de Soluções.

##  <a name="VersionSupport"></a> Suporte de edição para a arquitetura e ferramentas de modelagem

Visual Studio 2015 está disponível em várias edições. Nem todos eles oferecem suporte para a arquitetura e ferramentas de modelagem. A tabela a seguir mostra a disponibilidade de cada ferramenta.

|**Recurso**|**Enterprise**|**Professional**|**Comunidade**|**Express**|
|-----------------|--------------------|----------------------|-------------------|-----------------|
|**Mapas de código**|Sim|Só dá suporte à leitura e filtragem de mapas de código, adicionar novos nós genéricos e criando um novo gráfico direcionado a partir de uma seleção.|-|-|
|**Diagramas de classe UML**|Sim|-|-|-|
|**Diagramas de sequência UML**|Sim|-|-|-|
|**Diagramas de caso de uso UML**|Sim|-|-|-|
|**Diagramas de atividade UML**|Sim|-|-|-|
|**Diagramas de componente UML**|Sim|-|-|-|
|**Diagramas de camada**|Sim|-|-|-|
|**Gráficos direcionados** (diagramas DGML)|Sim|Sim|-|-|
|**Clone de código**|Sim|-|-|-|