---
title: Navegue e reorganize mapas de código | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.dgmlgraph.layouthelp
- vs.progression.graphdocument
- vs.progression.dgmlgraph.message.notUlt.noexpandgroup
- vs.progression.colorsetpicker
- vs.progression.iconsetpicker
helpviewer_keywords:
- Visual Studio Ultimate, dependency graphs
- code visualization [Visual Studio ALM]
- graph documents, browsing
- Visual Studio ALM, dependency graphs
- code visualization
- Visual Studio ALM, graph documents
- Visual Studio Ultimate, graph documents
- dependency graphs, browsing
ms.assetid: 08f65f77-6ca7-4b25-b060-3f6c9f5847a4
caps.latest.revision: 91
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3ecdfb91beb4d844216a9c961830af336e9de15a
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302353"
---
# <a name="browse-and-rearrange-code-maps"></a>Procurar e reorganizar mapas de código
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Reorganize itens em mapas de código para torná-los mais fáceis de ler e melhorar seu desempenho.

 Você pode personalizar mapas de código sem afetar o código subjacente em uma solução. Isso é útil quando você deseja se concentrar em elementos-chave do código ou comunicar idéias sobre o código. Por exemplo, para destacar áreas interessantes, você pode selecionar elementos de código no mapa e filtrá-los, alterar o estilo de elementos de código e links, ocultar ou excluir elementos de código e organizar elementos de código usando propriedades, categorias ou grupos.

 **Requisitos**

- Para criar mapas de código, você deve ter visual studio enterprise.

- Você pode visualizar mapas de código e fazer edições limitadas para mapas de código no Visual Studio Professional.

## <a name="get-started-working-with-code-maps"></a><a name="ManageLargeGraphs"></a>Comece a trabalhar com mapas de código
 Crie um mapa de código (consulte [as dependências do mapa em suas soluções](../modeling/map-dependencies-across-your-solutions.md) para obter mais detalhes). Se você não quiser esperar o mapa terminar de gerar, clique no link **Cancelar** a qualquer momento para interromper o processo de geração. No entanto, você não verá os detalhes de todas as dependências e links se fizer isso.

 Depois de gerar o mapa, comece com essas dicas para revisar seu código:

- Olhe para os aglomerados de dependência natural no código. Na barra de ferramentas do mapa, escolha **Layout**, botão **Clusters**![rápidos quick clusters na barra de ferramentas do gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon"). Veja [Alterar o layout do mapa](#Selecting).

     ![Gráfico de dependência &#45; layout de clusters rápidos](../modeling/media/dependencygraph-quickclusters.png "DependencyGraph_QuickClusters")

- Organize o mapa em áreas menores agrupando nódulos relacionados. Colapso esses grupos para ver apenas as dependências intergrupos, que aparecem automaticamente. Consulte [os nós do grupo](#OrganizeGroups).

- Use filtros para simplificar o mapa e se concentrar nos tipos de nós ou links que você está interessado. Consulte [Tecidas e links do filtro](#FilterNodes).

- Maximize o desempenho de grandes mapas. Consulte [as dependências do Mapa em suas soluções](../modeling/map-dependencies-across-your-solutions.md) para obter mais informações. Por exemplo, **ative skip build** na barra de ferramentas do mapa para que o Visual Studio não reconstrua sua solução quando você atualizar itens no mapa.

## <a name="change-the-map-layout"></a><a name="Selecting"></a>Alterar o layout do mapa

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Organize o fluxo de dependência para todo o mapa em uma direção específica. Isso pode ajudá-lo a ver camadas arquitetônicas no código.|Na barra de ferramentas do mapa, escolha **Layout**e, em seguida:<br /><br /> -   **Botão gráfico de cima para baixo** de cima para ![baixo](../modeling/media/topbottomgraphbutton.gif "Botão topbottomGraph")<br />-   **Botão gráfico de baixo para superior** para ![superior](../modeling/media/bottomtopgraphbutton.gif "Botão de bottomtopgraph")<br />-   **Botão de** layout da esquerda para a direita da ![esquerda para a direita](../modeling/media/leftrightgraphbutton.gif "Botão do gráfico à direita à esquerda")<br />-   **Botão gráfico da direita para a esquerda** da direita para a ![esquerda](../modeling/media/rightleftgraphbutton.gif "Botão de gráfico à esquerda direita")|
|Veja os clusters de dependência natural no código com os nódulos mais dependentes no centro dos clusters e os nódulos menos dependentes no exterior desses clusters.|Na barra de ferramentas do mapa, escolha **Layout**e, em seguida, botão **Clusters**![rápidos quick clusters na barra de ferramentas do gráfico](../modeling/media/quickclustersicon.gif "QuickClustersIcon").|
|Selecione um ou mais nós no mapa.|Clique em um nó para selecioná-lo. Para selecionar ou desmarcar mais de um nó, segure **CTRL** ao clicar.<br /><br /> Teclado: pressione **TAB** ou use as teclas de seta para mover o retângulo de foco pontilhado para um nó e pressione **SPACE** para selecioná-lo. Pressione **CTRL** + **SPACE** para vários nódulos de seleção ou desmarcação.|
|Mova nódulos específicos no mapa.|Arraste os nódulos para movê-los. Para mover outros nódulos e links para fora do caminho enquanto você arrasta os nós, pressione e segure a tecla **SHIFT.**<br /><br /> Teclado: segure **CTRL** e pressione as teclas de seta.|
|Altere o layout dentro de um grupo independentemente dos outros nódulos e grupos no mapa.|Selecione um nó e abra o menu de atalho. Escolha **Layout** e selecione um estilo de layout.<br /><br /> - ou -<br /><br /> Selecione um nó e expanda-o para mostrar os nódulos da criança. Clique no título do nó para mostrar a barra de ferramentas pop-up do grupo e abra o **estilo Alterar o layout do gráfico**dependência do grupo &#45; barra de ferramentas do grupo &#45; lista de![layout.](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") Selecione um dos layouts das árvores, **Clusters Rápidos**ou **Exibição de Lista** (que organiza o conteúdo do grupo em uma lista).<br /><br /> Consulte [os nós do grupo](#OrganizeGroups) para obter mais detalhes.|
|Desfaça uma ação no mapa.|Pressione **CTRL** + **Z** ou use o comando Visual Studio **Undo.**|

## <a name="browse-the-map"></a><a name="Explore"></a>Navegue pelo mapa

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Escaneie o mapa.|Arraste o mapa em qualquer direção usando o mouse.<br /><br /> - ou -<br /><br /> Segure **SHIFT** e gire a roda do mouse para rolar horizontalmente. Segure **SHIFT** + **CTRL** e gire a roda do mouse para rolar horizontalmente.|
|Aproxime-se ou saia do mapa.|Gire a roda do mouse.<br /><br /> - ou -<br /><br /> Use a lista de isto **Zoom** na barra de ferramentas do mapa de código.<br /><br /> - ou -<br /><br /> Use os atalhos do teclado. Para ampliar, pressione **CTRL + SHIFT + .** (ponto). Para diminuir o zoom, **pressione CTRL + SHIFT + ,** (comma).|
|Amplie uma área específica usando o mouse.|Segure o botão direito do mouse enquanto desenha um retângulo em torno dessa área que você está interessado.|
|Redimensione e encaixe o mapa em sua janela.|Escolha **Zoom para encaixar** na lista **Zoom** na barra de ferramentas do mapa de código.<br /><br /> - ou -<br /><br /> Clique no **ícone Zoom para caber** no ícone Zoom na barra de ferramentas do ![mapa](../modeling/media/almcodemapzoomicon.png "ALMCodeMapZoomIcon") na barra de ferramentas do mapa de código. Teclado: **pressione CTRL + 0** (zero).|
|Encontre um nó no mapa pelo nome. **Dica:**  Isso funciona apenas para itens no mapa. Para encontrar itens em sua solução, mas não no mapa, encontre-os no **Solution Explorer**e arraste-os para o mapa. (Arraste sua seleção ou na barra de ferramentas do Solution Explorer, clique **em Mostrar no Mapa de Código**).|1. Escolha o ícone **Encontrar** ![encontrar ícone na barra de ferramentas](../modeling/media/almcodemapfindicon.png "ALMCodeMapFindIcon") do mapa na barra de ferramentas do mapa de código (Teclado: pressione **CTRL + F**) para mostrar a caixa de pesquisa no canto superior direito do mapa.<br />2. Digite o nome do item e **pressione Retornar** ou clique no ícone "lupa". O primeiro item que corresponde à sua pesquisa aparece selecionado no mapa.<br />3. Para personalizar sua pesquisa, abra a lista de paradas e escolha uma opção de pesquisa. As opções são **Find Next**, **Find Previous**e Select **All**. Em seguida, clique no botão correspondente ao lado da caixa de texto de pesquisa.<br />     ![As opções de pesquisa&#45;lista para baixo](../modeling/media/almcodemapssearchdropdown.png "ALMCodeMapsSearchDropDown")<br />     Alternativamente, use o teclado: pressione **F3** para selecionar o próximo nó correspondente ou **SHIFT + F3** para selecionar o nó correspondente anterior.<br />4. Selecione qualquer uma das opções que especificam como os termos de pesquisa são tratados clicando nos ícones abaixo da caixa de texto de pesquisa.<br />     ![Opções de correspondência de pesquisa](../modeling/media/almcodemapssearchmatchicons.png "ALMCodeMapsSearchMatchÍcones")<br />     As opções são, da esquerda para a direita, correspondência sensível ao caso, corresponder apenas palavras inteiras, usar sintaxe de expressão regular .NET, expandir automaticamente grupos para mostrar correspondências para itens fechados. **Importante:**  Você pode usar a caixa de pesquisa para encontrar correspondências em grupos colapsados apenas se esses grupos foram expandidos anteriormente. Para encontrar essas correspondências e expandir seus grupos-pai automaticamente, escolha esta opção na caixa de pesquisa.|
|Selecione todos os nós não selecionados.|Abra o menu de atalho para os nós selecionados. Escolha **Selecionar**, **Inverter Seleção**.|
|Selecione os nós adicionais que se vinculam aos selecionados.|Abra o menu de atalho para os nós selecionados. Escolha **Selecionar** e um deles:<br /><br /> - Para selecionar os nós adicionais que se vinculam diretamente ao nó selecionado, escolha **Dependências recebidas**.<br />- Para selecionar os nós adicionais que se vinculam diretamente ao nó selecionado, escolha **Dependências de saída**.<br />- Para selecionar nós adicionais que se vinculam diretamente ao nó selecionado, escolha **Ambos**.<br />- Para selecionar todos os nós que vinculam e do nó selecionado, escolha **Subgrafo conectado**.<br />- Para selecionar todas as crianças do nó selecionado, escolha **Crianças**.|

## <a name="filter-nodes-and-links"></a><a name="FilterNodes"></a>Filés e links de filtro

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Mostre ou esconda o painel Filtros.|Escolha o botão **Filtros** na barra de ferramentas do mapa de código. O painel Filtros é exibido como uma página com guias na janela Solution Explorer por padrão.|
|Filtre os tipos de nós mostrados no mapa.|Defina ou limpe as caixas de seleção na lista **Elementos de código** no painel Filtros.|
|Filtre os tipos de links mostrados no mapa.|Defina ou limpe as caixas de seleção na lista **Relacionamentos** no painel Filtros.|
|Mostrar ou ocultar os nós do projeto de teste no mapa.|Defina ou limpe a caixa de seleção Ativos de **Teste** na lista **Diversas** no painel Filtros.|

 Os ícones mostrados no painel Legenda do mapa refletem as configurações que você faz na lista. Para mostrar ou ocultar o painel Legenda, clique no botão **Legenda** na barra de ferramentas do mapa de código.

## <a name="examine-nodes-and-links"></a><a name="Inspect"></a>Examine os nódulos e links
 Mapas de código mostram esses tipos de links:

- Um link individual representa uma única relação entre dois nós.

- Um link entre grupos representa uma relação entre dois nós em grupos diferentes.

- Um elo agregado representa todas as relações que apontam na mesma direção entre dois grupos.

> [!TIP]
> Por padrão, o mapa mostra links de grupo cruzado apenas para nós selecionados. Para alterar esse comportamento para mostrar ou ocultar links agregados entre grupos, clique em **Layout** na barra de ferramentas do mapa de código e escolha **Avançado,** em seguida, **mostrar todos os links de grupo cruzado** ou **ocultar todos os links de grupos cruzados**. Consulte [Ocultar ou mostrar nós e links](#HidingShowing) para obter mais detalhes.

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Veja mais informações sobre um nó ou um link.|Mova o ponteiro do mouse na parte superior do nó ou link até que uma dica de ferramenta apareça.<br /><br /> A dica de ferramenta para um link agregado lista as dependências individuais que ele representa.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para o nó ou o link. Escolha **Editar**, **Propriedades**.|
|Mostrar ou ocultar o conteúdo de um grupo.|- Para expandir um grupo, abra o menu de atalho para o nó e escolha **Grupo**, **Expanda**.<br />     - ou -<br />     Mova o ponteiro do mouse na parte superior do nó até que o botão chevron (seta para baixo) apareça. Clique neste botão para expandir o grupo. Teclado: para expandir ou colapsar **PLUS** o**+** grupo selecionado, pressione a tecla PLUS ( ) ou a tecla **MINUS** ().**-**<br />- Para desabar um grupo, abra o menu de atalho para o nó e escolha **Grupo**, **Colapso**.<br />     - ou -<br />     Mova o ponteiro do mouse em cima de um grupo até que o botão chevron (seta para cima) apareça. Clique neste botão para colapsar o grupo.<br />- Para expandir todos os grupos, **pressione CTRL** + **A** para selecionar todos os nós. Abra o menu de atalho para o mapa e escolha **Grupo**, **Expanda**. **Nota:**      Este comando não está disponível se a expansão de todos os grupos gerar um mapa ou problemas de memória inutilizáveis. Recomenda-se que você expanda o mapa apenas para o nível de detalhes que você se importa.<br />- Para colapsar todos os grupos, abra o menu de atalho para um nó ou para o mapa. Escolher **grupo**, **colapsar tudo**.|
|Consulte a definição de código para um namespace, tipo ou membro.|Abra o menu de atalho para o nó e escolha **Ir para Definição**.<br /><br /> -ou-<br /><br /> Clique duas vezes no nó. Para grupos expandidos, clique duas vezes no cabeçalho do grupo.<br /><br /> -ou-<br /><br /> Selecione o nó e pressione **F12**.<br /><br /> Por exemplo: <br /><br /> - Para um namespace contendo uma classe, o arquivo de código da classe é aberto para mostrar a definição dessa classe. Em outros casos, a janela **Encontrar resultados de símbolos** mostra uma lista de arquivos de código. **Nota:**      Quando você executa essa tarefa em um espaço de nome Visual Basic .NET, o arquivo de código por trás do namespace não é aberto. Esse problema também ocorre quando você executa essa tarefa em um grupo de nós selecionados que incluem um espaço de nome Visual Basic .NET. Para contornar esse problema, navegue manualmente até o arquivo de código por trás do namespace ou omita o nó para o namespace da sua seleção.<br />- Para uma classe ou uma classe parcial, o arquivo de código dessa classe é aberto para mostrar a definição da classe.<br />- Para um método, o arquivo de código da classe pai é aberto para mostrar a definição do método.|
|Examine dependências e itens que participam de um link agregado.|Selecione os links que você está interessado e abra o menu de atalho para sua seleção. Escolha **Mostrar links contribuintes** ou **mostrar links contribuintes no novo mapa de código**.<br /><br /> O Visual Studio expande os grupos em ambas as extremidades do link e mostra apenas esses itens e dependências que participam do link. **Nota:**  Quando você examina dependências entre itens em grupos parciais, você pode ver esse comportamento: <ul><li>Links para itens que não participam do exame desaparecem do mapa, mesmo que esses links ainda existam.</li><li>Suponha que você examine um link para um item em um grupo parcial e, em seguida, examine um link diferente para o mesmo item. Durante o segundo exame, o grupo parcial alvo mostra apenas itens do seu primeiro exame. Links e itens-alvo que não participaram do seu primeiro exame, mas participam do seu segundo exame, não aparecem.</li></ul> Para ver itens perdidos de um grupo, escolha **Refetch Children**![Refetch Children Icon](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") (que indica que nem todos os membros de um grupo aparecem no mapa). Você também pode tentar desfazer suas ações (Teclado: pressione **CTRL+Z**) e examinar as dependências de um novo mapa.|
|Examine dependências em vários léus em diferentes grupos.|Expanda os grupos para que você possa ver todos os seus filhos. Selecione todos os nós que lhe interessam, incluindo seus filhos. O mapa mostra os links de grupo cruzado entre os nós selecionados.<br /><br /> Para selecionar todos os nós em um grupo, pressione e segure **SHIFT** e o botão esquerdo do mouse enquanto você desenha um retângulo em torno desse grupo. Para selecionar todos os nós em um mapa, **pressione CTRL**+**A**. **Dica:**  Para mostrar links entre grupos o tempo todo, escolha **Layout** na barra de ferramentas do mapa, **Avançado**, **Mostrar todos os links de grupo cruzado**.|
|Consulte os itens que um nó ou referências de link.|Abra o menu de atalho para o nó e escolha **Encontrar todas as referências**. **Nota:**  Isso só se `Reference` aplica quando o atributo é definido para o nó ou link no arquivo .dgml do mapa. Para adicionar referências a itens de nomes ou links, consulte [Personalizar mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).|

## <a name="hide-or-show-nodes-and-links"></a><a name="HidingShowing"></a>Ocultar ou mostrar nódulos e links
 Ocultar nós os impede de participar de algoritmos de layout. Por padrão, links de grupo cruzado permanecem ocultos. Links de grupo cruzado são links individuais que conectam nós entre os grupos. Quando os grupos são colapsados, o mapa agrega todos os links entre grupos em links únicos entre grupos. Quando você expande um grupo e seleciona nós dentro do grupo, os links de grupo cruzado são exibidos e mostram as dependências nesse grupo.

> [!CAUTION]
> Antes de compartilhar um mapa criado no Visual Studio Enterprise com aqueles que usam o Visual Studio Professional, certifique-se de desocultar quaisquer nomes ou links de grupo cruzado que você deseja que outros vejam. Do contrário, os usuários não poderão reexibir esses itens.

### <a name="to-hide-or-show-nodes"></a>Para ocultar ou mostrar nós

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Ocultar os nódulos selecionados.|1. Selecione os nós que deseja esconder.<br />2. Abra o menu de atalho para os nós selecionados ou para o mapa. Escolha **Selecionar,** **Ocultar selecionado**.|
|Ocultar nódulos não selecionados.|1. Selecione os pontos que deseja permanecer visíveis.<br />2. Abra o menu de atalho para os nós selecionados ou para o mapa. Selecione **Selecionar,** **Ocultar Não Selecionado**.|
|Mostre nódulos escondidos.|- Para mostrar todos os nós escondidos dentro de um grupo, primeiro certifique-se de que o grupo seja expandido. Abra o menu de atalho e escolha **Selecionar**, **Desocultar crianças**.<br />     - ou -<br />     Clique no ícone **Unhide Children**![Unhide Children](../modeling/media/dependencygraph-filtericon-hiddennodes.gif "DependencyGraph_FilterIcon_HiddenNodes") no canto superior esquerdo do grupo (isso só é visível quando há nós de crianças ocultas).<br />- Para mostrar todos os nós ocultos, abra o menu de atalho para o mapa ou um nó e escolha **Selecionar**, **Desocultar tudo**.|

### <a name="to-hide-or-show-links"></a>Para ocultar ou mostrar links

|**Para**|**Na barra de ferramentas do mapa, escolha Layout, Avançado e escolha**|
|------------|----------------------------------------------------------------------|
|Mostrar links de grupos cruzados o tempo todo.|**Mostrar todos os links de grupos cruzados**. Isso oculta links agregados entre grupos.|
|Ocultar links de grupos cruzados o tempo todo.|**Ocultar todos os links de grupos cruzados**|
|Mostrar somente links de grupo cruzado para nós selecionados.|**Mostrar Links de Grupo Cruzado em Nós Selecionados**|
|Esconda todos os links.|**Ocultar todos os links**. Para mostrar links novamente, escolha uma das opções listadas acima.|

## <a name="group-nodes"></a><a name="OrganizeGroups"></a>Nódulos de grupo

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Mostrar os nós do contêiner como nós de grupo ou nós de folha.|Para mostrar os nós do contêiner como nó de folha: selecione os nós, abra o menu de atalho para sua seleção e escolha **Grupo**, **Converta para Folha**.<br /><br /> Para mostrar os nós de contêiner como nó de grupo: selecione os nós, abra o menu de atalho para sua seleção e escolha **Grupo**, **Converta para Grupo**.|
|Altere o layout dentro de um grupo.|Selecione o grupo, abra o menu de atalho, escolha **Layout**e selecione o estilo de layout desejado.<br /><br /> - ou -<br /><br /> 1. Selecione o grupo e certifique-se de que ele está expandido.<br />2. Clique no cabeçalho do grupo novamente e a barra de ferramentas do grupo aparecerá.<br />     ![Gráfico de dependência &#45; barra de ferramentas de grupo](../modeling/media/dependencygraph-group.png "DependencyGraph_Group")<br />3. Abra o **estilo Alterar o layout do** gráfico de dependência da lista de grupos &#45; barra de ferramentas de grupo &#45; ![layout](../modeling/media/dependencygraph-grouptoolbar.gif "DependencyGraph_GroupToolbar") e escolha o estilo de layout desejado.<br /><br /> **A exibição de** listas reorganiza os membros do grupo na lista. **O Gráfico Padrão** redefine o layout do grupo para o layout padrão do mapa. Para outras opções, consulte [Alterar o layout do mapa](#Selecting).|
|Adicione um nó a um grupo.|Arraste o nó para o grupo.<br /><br /> Enquanto você arrasta o nó, o Visual Studio exibe um indicador para mostrar que você está movendo o nó.<br /><br /> Também é possível arrastar nós para fora de um grupo.|
|Adicione um nó a um nó não-grupo.|Arraste o nó para o nó de destino. Você pode converter qualquer nó de destino em um grupo adicionando nós a ele.|
|Grupo de nódulos selecionados.|1. Selecione os nós que deseja agrupar. Uma barra de ferramentas pop-up aparece acima do último nó selecionado.<br />     ![Barra de ferramentas do gráfico de dependência](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. Na barra de ferramentas, escolha o quarto ícone **Agrupar os nós selecionados** (se o nó for expandido, ele terá cinco em vez de quatro ícones). Digite o nome para o novo grupo e **pressione Return**.<br />     - ou -<br />     Selecione os nós que deseja agrupar e abra o menu de atalho para sua seleção. Escolha **Grupo**, **Adicionar grupo pai,** digite o nome para o novo grupo e **pressione Return**.<br /><br /> Você pode renomear um grupo. Abra o menu de atalho para o grupo e escolha **Editar**, **Propriedades** para abrir a janela Propriedades do Estúdio Visual. Na propriedade **Label,** renomeie o grupo conforme necessário.|
|Remova grupos.|Selecione o grupo ou os grupos que você deseja remover. Abra o menu de atalho para sua seleção e escolha **Grupo**, **Remover grupo**.|
|Remova os nódulos do grupo dos pais.|Selecione os nós que você deseja mover. Abra o menu de atalho para sua seleção e escolha **Grupo**, **Remover do pai**. Isso remove os nódulos até seus avós, ou para fora do grupo se eles não tiverem um grupo de avós.<br /><br /> - ou -<br /><br /> Selecione os nódulos e arraste-os para fora do grupo.|

## <a name="add-remove-or-rename-nodes-links-and-comments"></a><a name="AddRemoveNodesLinks"></a>Adicionar, remover ou renomear nomes, links e comentários
 Você pode exibir mais ou menos itens em um mapa para detalhar ou simplificar o mapa. Você também pode renomear itens e adicionar comentários aos itens.

> [!CAUTION]
> Antes de compartilhar um mapa que foi criado usando o Visual Studio Enterprise com aqueles que usam o Visual Professional, certifique-se de que quaisquer elementos de código que você queira que outros vejam estão visíveis no mapa. Caso contrário, esses usuários não serão capazes de recuperar elementos de código excluídos.

### <a name="add-a-node-for-a-code-element"></a>Adicione um nó para um elemento de código

|**Para**|**Realizar estas etapas**|
|------------|-----------------------------|
|Adicione um novo nó genérico no local atual do ponteiro do mouse.|1. Mova o ponteiro do mouse para o lugar no mapa onde deseja colocar o novo elemento de código e **pressione Inserir**.<br />     - ou -<br />     Abra o menu de atalho para o mapa e escolha **Editar**, **Adicionar**, **Nó genérico**.<br />2. Digite o nome do novo nó e **pressione Return**.|
|Adicione um tipo específico de nó de elemento de código no local atual do ponteiro do mouse.|1. Mova o ponteiro do mouse para o lugar no mapa onde você deseja colocar o novo elemento de código e abra o menu de atalho para o mapa.<br />2. Escolha **Editar,** **Adicionar**e selecionar o tipo de nó desejado.<br />3. Digite o nome do novo nó e **pressione Return**.|
|Adicione um nó genérico ou um tipo específico de elemento de código a um grupo.|1. Selecione o nó de grupo e abra o menu de atalho.<br />2. Escolha **Editar,** **Adicionar**e selecionar o tipo de nó desejado.<br />3. Digite o nome do novo nó e **pressione Return**.|
|Adicione um novo nó do mesmo tipo e vinculado a um nó existente.|1. Selecione o elemento de código. Uma barra de ferramentas pop-up aparece acima dela.<br />     ![Barra de ferramentas do gráfico de dependência](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")<br />2. Na barra de ferramentas, escolha o segundo ícone **Criar um nó com a mesma categoria deste nó e adicionar um novo link a ele**.<br />3. Escolha um lugar no mapa para colocar o novo elemento de código e clique no botão esquerdo do mouse.<br />4. Digite o nome do novo nó e **pressione Return**.|
|Adicione um novo nó genérico que está vinculado a partir de um elemento de código existente que tem foco.|1. Usando o teclado, **pressione Tab** até que o elemento de código para vincular tenha o foco (retângulo pontilhado).<br />2. Pressione **Alt**+**Insert**.<br />3. Digite o nome do novo nó e **pressione Return**.|
|Adicione um novo nó genérico que se vincula a um elemento de código existente que tem foco.|1. Usando o teclado, **pressione Tab** até que o elemento de código para vincular tenha o foco (retângulo pontilhado).<br />2. Pressione **alt**+**shift**+**insert**.<br />3. Digite o nome do novo nó e **pressione Return**.|

|**Para adicionar elementos de código para**|**Realizar estas etapas**|
|----------------------------------|-----------------------------|
|Elementos de código na solução.|1. Encontre o elemento de código no **Solution Explorer**. Use a caixa de pesquisa **do Solution Explorer** ou navegue pela solução. **Dica:**      Para encontrar elementos de código que tenham dependências de um tipo ou de um membro, abra o menu de atalho para o tipo ou o membro no **Solution Explorer**. Escolha a relação que lhe interessa. **O Solution Explorer** mostra apenas esses elementos de código com as dependências especificadas.<br />2. Arraste os elementos de código que lhe interessam até a superfície do mapa. Você também pode arrastar elementos de código do Class View ou do Object Browser.<br />     - ou -<br />     No **Solution Explorer,** selecione os elementos de código que deseja mapear. Em seguida, na barra de ferramentas **do Solution Explorer,** clique **em Mostrar no Mapa de Código**.<br /><br /> Por padrão, a hierarquia de contêiner pai para os novos elementos de código é mostrada no mapa. Use o botão **Incluir pais** na barra de ferramentas do mapa de código para alterar esse comportamento. Quando desligado, apenas o elemento de código em si é adicionado ao mapa. Para reverter esse comportamento para apenas uma ação de arrastar e soltar, pressione e segure a tecla **CTRL** enquanto arrasta os elementos de código para o mapa.<br /><br /> O Visual Studio adiciona elementos de código para os elementos de código de nível superior em sua seleção. Para ver se um elemento de código contém outros elementos de código, mova o ponteiro do mouse na parte superior do elemento de código para que o chevron (seta para baixo) apareça. Escolha o chevron para expandir o elemento de código. Para expandir todos os elementos de código, **pressione CTRL**+**A** para selecionar todos os elementos, abra o menu de atalho para o mapa e escolha **Grupo**, **Expanda**. Este comando não está disponível se a expansão de todos os grupos produzirum mapa inutilizável ou causar escassez de problemas de memória.|
|Elementos de código relacionados com elementos de código no mapa.|Clique no botão **Mostrar Relacionado** na barra de ferramentas do mapa de código e escolha o tipo de itens relacionados que você está interessado.<br /><br /> - ou -<br /><br /> Abra o menu de atalho para o elemento código. Escolha um dos **shows...** itens no menu, dependendo do tipo de relacionamento que lhe interessa. Por exemplo, você pode ver itens que o item atual faz referência, itens que fazem referência ao item atual, aos tipos base e derivados para classes, chamadores de métodos e as classes, espaços de nome e conjuntos que contêm.<br /><br /> Para mais detalhes, consulte [este tópico](../modeling/map-dependencies-across-your-solutions.md).|
|Conjuntos .NET compilados (.dll ou .exe) ou binários.|Arraste as montagens ou binários de fora do Visual Studio para um mapa.<br /><br /> Você pode arrastar do Windows Explorer ou do File Explorer somente se estiver executando-o e o Visual Studio no mesmo nível de permissões do User Access Control (UAC). Por exemplo, se o UAC estiver ligado e você estiver executando o Visual Studio como Administrador, o Windows Explorer ou o File Explorer bloquearão a operação de arrasto.|

### <a name="AddNodes"></a>
##### <a name="add-a-link-between-existing-code-elements"></a>Adicione um link entre os elementos de código existentes

1. Selecione o elemento de código fonte. Uma barra de ferramentas aparece acima do elemento de código.

    ![Barra de ferramentas do gráfico de dependência](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. Na barra de ferramentas, escolha o primeiro ícone, **Crie um novo link a partir deste nó para o nó em que você clicar em seguir**.

3. Selecione o elemento de código de destino. Um link aparece entre os dois elementos de código.

   \- ou –

4. Selecione o elemento de código-fonte no mapa.

5. Se você tiver um mouse instalado, mova o ponteiro do mouse para fora dos limites do mapa.

6. Abra o menu de atalho do elemento de código e escolha **Editar,** **Adicionar,** **Vincular genérico.**

7. Guia e selecione o elemento de código de destino para o link.

8. Pressione **RETURN**.

### <a name="AddComments"></a>
##### <a name="add-a-comment-to-an-existing-node-on-the-map"></a>Adicione um comentário a um nó existente no mapa

1. Selecione o elemento de código. Uma barra de ferramentas aparece acima dela.

     ![Barra de ferramentas do gráfico de dependência](../modeling/media/depedencygraph-toolbar.png "DepedencyGraph_Toolbar")

2. Na barra de ferramentas, escolha o terceiro ícone, **Crie um novo nó de comentário com um novo link para o nó selecionado**.

     \- ou –

     Abra o menu de atalho para o elemento código e escolha **Editar**, **Novo comentário**.

3. Digite os comentários. Para digitar uma nova linha, **pressione SHIFT** + **RETURN**.

##### <a name="add-a-comment-to-the-map-itself"></a>Adicione um comentário ao próprio mapa

1. Abra o menu de atalho para o mapa e escolha **Editar**, **Novo comentário**.

2. Digite os comentários. Para digitar uma nova linha, **pressione SHIFT** + **RETURN**.

### <a name="RenameNodes"></a>
##### <a name="rename-a-code-element-or-link"></a>Renomeie um elemento de código ou link

1. Selecione o elemento de código ou o link que deseja renomear.

2. Pressione **F2**ou abra o menu de atalho e escolha **Editar**, **Renomear**.

3. Quando a caixa de edição aparecer no mapa, renomeie o elemento de código ou o link.

     \- ou –

4. Abra o menu de atalho e escolha **Editar**, **Propriedades**.

5. Edite a propriedade **Label** na janela Propriedades do Visual Studio.

##### <a name="remove-a-code-element-or-link-from-the-map"></a>Remova um elemento de código ou link do mapa

1. Selecione o elemento de código ou link e pressione a **tecla Excluir.**

     \- ou –

     Abra o menu de atalho para o elemento de código ou link e escolha **Editar**, **Remover**.

2. Se o elemento ou link fizer parte de um grupo, o botão **Refetch Children** ![Refetch Children será](../modeling/media/dependencygraph-deletednodesicon.png "DependencyGraph_DeletedNodesIcon") exibido dentro do grupo. Clique aqui para recuperar elementos e links perdidos.

- Você pode remover elementos de código e links de um mapa sem afetar o código subjacente. Quando você os exclui, suas definições são removidas do arquivo DGML (.dgml).

- Mapas criados pela edição do DGML, adicionando elementos de código indefinidos, ou usando algumas versões anteriores do Visual Studio, não suportam esse recurso.

##### <a name="flag-a-code-element-for-follow-up"></a>Sinalizar um elemento de código para acompanhamento

1. Selecione o elemento de código ou link que deseja sinalizar para acompanhamento.

2. Abra o menu de atalho e escolha **Editar**, **Flag para Acompanhar**.

- Por padrão, o elemento código ganha um fundo vermelho. Considere [adicionar um comentário](#AddComments) a ele com as informações de acompanhamento apropriadas.

- Altere a cor de fundo do elemento ou limpe o sinalizador de seguimento escolhendo **Editar**, **Outras cores de bandeira**.

## <a name="change-the-style-of-a-code-element-or-link"></a><a name="ChangeStyleCodeOrLink"></a>Alterar o estilo de um elemento de código ou link
 Você pode alterar os ícones em elementos de código e as cores de elementos de código e links usando ícones e cores predefinidos. Por exemplo, você pode escolher uma cor para destacar elementos de código e links que tenham uma determinada categoria ou propriedade. Isso permite que você identifique e se concentre em áreas específicas do mapa. Você pode especificar ícones e cores personalizadas editando o arquivo .dgml do mapa; ver [Personalizar mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

#### <a name="to-apply-a-predefined-color-or-icon-to-code-elements-or-links-with-a-certain-category-or-property"></a>Para aplicar uma cor ou ícone predefinido a elementos de código ou links com uma determinada categoria ou propriedade

1. Na barra de ferramentas do mapa, escolha **Legend**.

2. Na caixa **Legend,** veja se a categoria ou propriedade do elemento de código já aparece na lista.

3. Se a lista não incluir a **+** categoria ou propriedade, escolha na caixa **Legenda** e escolha **'Propriedade de**nó '' **Nacategoria**, **'Propriedade de link'** ou **categoria Link**. Em seguida, escolha a propriedade ou categoria. A categoria ou propriedade agora aparece na caixa **Legenda.**

    > [!NOTE]
    > Para criar e atribuir uma categoria ou uma propriedade a um elemento de código, você pode editar o arquivo .dgml do mapa; ver [Personalizar mapas de código editando os arquivos DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md).

4. Na caixa **Legenda,** clique no ícone ao lado da categoria ou propriedade adicionada ou deseja alterar.

5. Use a tabela a seguir para selecionar o estilo que você deseja alterar:

    |**Para alterar a**|**Escolher**|
    |-----------------------|----------------|
    |Cor do plano de fundo|**Fundo**|
    |Cor do contorno|**Curso**|
    |Cor de texto (uma letra "f" é exibida para mostrar o resultado)|**Primeiro**|
    |ícone|**Ícones**|

     A caixa de diálogo **Seletor de conjunto de cores** ou **seletor de ícones** é exibida para você selecionar uma cor ou ícone.

6. Na caixa de diálogo **Seletor de conjunto de cores** ou de seleção de conjunto de **ícones,** faça um dos seguintes:

    |**Para aplicar um**|**Realizar estas etapas**|
    |--------------------|-----------------------------|
    |Conjunto de cores ou ícones|Abra a lista de **configuração** **Selecionar cor** (ou **ícone).** Selecione um conjunto de cores ou ícones.|
    |Cor ou ícone específico|Abra a categoria ou a lista de valores da propriedade. Selecione uma cor ou ícone.|

    > [!NOTE]
    > Você pode reorganizar, excluir ou desativar temporariamente estilos na caixa **Legenda.** Consulte [Editar a caixa Legenda](#ModifyLegend).

## <a name="edit-the-legend-box"></a><a name="ModifyLegend"></a>Editar a caixa Legenda
 Você pode reorganizar, excluir ou desativar temporariamente estilos na caixa **Legenda:**

1. Abra o menu de atalho para um estilo na caixa **Legend.**

2. Realize uma das seguintes tarefas:

    |**Para**|**Escolher**|
    |------------|----------------|
    |Desativar o elemento de código|**Disable**|
    |Exclua o elemento de código|**Excluir**|
    |Mover o estilo para cima|**Mover para Cima**|
    |Mova o elemento de código para baixo|**Mover para Baixo**|

## <a name="copy-styles-from-one-map-to-another"></a><a name="CopyLegend"></a>Copiar estilos de um mapa para outro

1. Certifique-se de que a **caixa Legend** seja exibida no mapa de origem. Se não estiver visível, na barra de ferramentas do mapa, clique em **Legenda**.

2. Abra o menu de atalho para a caixa **Legend.** Escolha **A legenda da cópia**.

3. Cole a lenda no mapa do alvo.

## <a name="merge-code-maps"></a><a name="MergeMaps"></a>Mesclar mapas de código
 Você pode mesclar mapas copiando e colando elementos de código entre mapas. Se os identificadores do elemento de código coincidirem, então colar elementos de código funciona como uma operação de mesclagem. Para facilitar essa tarefa, coloque todos os conjuntos ou binários que você deseja visualizar na mesma pasta para que o caminho completo de cada montagem ou binário seja o mesmo para cada mapa que você deseja mesclar.

 Alternativamente, você pode arrastar esses conjuntos ou binários para o mesmo mapa a partir dessa pasta.

## <a name="see-also"></a>Consulte Também
 [Dependências de mapas em suas soluções](../modeling/map-dependencies-across-your-solutions.md) [Use mapas de código para depurar seus aplicativos](../modeling/use-code-maps-to-debug-your-applications.md) Encontre [problemas potenciais usando analisadores de mapas de código](../modeling/find-potential-problems-using-code-map-analyzers.md) Personalize mapas de código editando a referência [dgml arquivos](../modeling/customize-code-maps-by-editing-the-dgml-files.md) Directed Graph [Markup Language (DGML)](../modeling/directed-graph-markup-language-dgml-reference.md)