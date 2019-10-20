---
title: Editar diagramas e modelos UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.modelingproject
- vs.teamarch.UMLModelExplorer
- vs.teamarch.UMLModelExplorer.rootnode
helpviewer_keywords:
- diagrams - modeling
- UML, copy and paste
- UML, models
- UML model
- UML, element properties
- UML
- UML, diagrams
ms.assetid: 87affd40-8127-4ee9-9d3a-ad977abe2ed6
caps.latest.revision: 86
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6585fbfa7c16e710633e81841b4c8eb380f9f564
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669719"
---
# <a name="edit-uml-models-and-diagrams"></a>Editar modelos e diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode criar e editar um modelo UML por meio dos modos de exibição fornecidos por vários tipos diferentes de diagrama. Ao fornecer perspectivas diferentes em seu sistema, esses diagramas ajudam você a entender e discutir diferentes aspectos de seu design e requisitos. O Visual Studio fornece modelos para cinco dos tipos de diagramas UML usados com mais frequência.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Este tópico descreve as técnicas para editar o modelo que são comuns entre os diferentes tipos de diagrama. Para obter mais informações específicas para tipos específicos de diagramas, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).

## <a name="in-this-topic"></a>Neste tópico

- [Os diagramas UML são modos de exibição de um modelo UML](#Views)

- [Criando diagramas de modelagem UML](#Creating)

- [Desenho de diagramas de modelagem UML](#Drawing)

- [Editando formas e conectores](#Editing)

- [Desfazendo alterações no modelo](#Undo)

- [Compartilhando elementos entre diagramas](#Sharing)

- [Copiando elementos e grupos de elementos relacionados](#Copying)

- [Excluindo um elemento de modelo ou suas exibições](#Deleting)

- [Pesquisando texto em um diagrama](#Searching)

- [Preparando um diagrama para apresentação](#presentation)

- [Estendendo os designers UML](#extensions)

## <a name="Views"></a>Os diagramas UML são modos de exibição de um modelo UML
 Você pode criar e usar diagramas UML somente em projetos de modelagem. Para obter mais informações sobre como criar diagramas e projetos, consulte [criar diagramas e projetos de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

- Um projeto de modelagem contém um único modelo UML. Cada diagrama UML no projeto é uma exibição do modelo UML.

- Você pode ver o modelo no **Gerenciador de modelos UML**. No menu **arquitetura** , aponte para **Windows**e clique em Gerenciador de **modelos UML**.

- Cada forma em um diagrama é uma exibição de um elemento no modelo. Quando você coloca uma nova forma em um diagrama, você está criando um novo elemento no modelo.

- Quando você salva qualquer diagrama, o Visual Studio salva todo o modelo, todos os seus diagramas e o arquivo de projeto de modelagem.

## <a name="Creating"></a>Criando diagramas de modelagem UML

1. No menu **arquitetura** do Visual Studio, clique em **novo UML ou diagrama de camada**.

2. Selecione e nomeie seu diagrama.

3. Em **Adicionar ao projeto de modelagem**, selecione um projeto de modelagem existente ou selecione **criar um novo projeto de modelagem**.

   > [!NOTE]
   > Um diagrama de modelagem deve existir dentro de um projeto de modelagem.

   Você também pode adicionar um diagrama a um projeto de modelagem existente no Gerenciador de Soluções. Clique com o botão direito do mouse no projeto de modelagem, aponte para **Adicionar**e clique em **novo item**.

#### <a name="to-create-an-empty-uml-modeling-project"></a>Para criar um projeto de modelagem UML vazio

- No menu **arquivo** , aponte para **novo**, clique em **projeto**e, na caixa de diálogo **novo projeto** , clique duas vezes em **modelagem projetos**.

  Para obter mais informações sobre como gerenciar projetos de modelagem, consulte [criar diagramas e projetos de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md).

## <a name="Drawing"></a>Desenho de diagramas de modelagem UML
 Um diagrama de modelagem exibe uma coleção de elementos de modelo vinculados por relações. Cada elemento é exibido como uma forma e cada relação é exibida como um conector entre duas formas.

 Há dois tipos de ferramentas, um para elementos e outro para relações. Por exemplo, na caixa de ferramentas do diagrama de classes UML, a **classe** é uma ferramenta de elemento e a **Associação** é uma ferramenta de relação.

> [!NOTE]
> Se você quiser informações específicas para tipos de diagramas específicos, consulte [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md).

#### <a name="to-create-elements-and-relationships-in-a-uml-modeling-diagram"></a>Para criar elementos e relações em um diagrama de modelagem UML

1. Para criar um elemento de modelo, clique em uma ferramenta de elemento na caixa de ferramentas e, em seguida, clique no diagrama onde você deseja que ele apareça. Depois de criar o elemento, ajuste seu tamanho e forma arrastando suas alças.

    Em alguns casos, você pode posicionar um novo elemento dentro de outro elemento. Por exemplo, em um diagrama de classes UML, você pode posicionar uma classe dentro de um pacote.

   > [!NOTE]
   > Se você não conseguir ver a caixa de ferramentas, clique em **caixa de ferramentas** no menu **Exibir** .

2. Para criar uma relação, clique em uma ferramenta de relação, clique no elemento em que você deseja que a relação seja iniciada e clique no elemento onde deseja que ela termine.

    Tipos diferentes de relações podem começar ou terminar em diferentes tipos de elementos. Por exemplo, em um diagrama de classes UML, uma relação de associação não pode iniciar ou terminar em um elemento de comentário.

   > [!NOTE]
   > Para usar a mesma ferramenta várias vezes, clique duas vezes na ferramenta. Quando tiver terminado, clique na ferramenta **ponteiro** .

   Em alguns tipos de diagramas, você também pode desenhar formas simples. Essas formas não fazem parte do modelo, mas você pode usá-las para chamar a atenção para partes do diagrama ou dividi-las em diferentes áreas.

## <a name="Editing"></a>Editando formas e conectores
 Ao redimensionar ou colorir uma forma ou redirecionar um conector, não há nenhum efeito sobre o modelo subjacente. No entanto, quando você renomeia uma forma no diagrama ou no Gerenciador de modelos UML, o elemento correspondente é renomeado no Gerenciador de modelos UML e em outros diagramas que apresentam esse elemento.

> [!NOTE]
> Há uma maneira simples de criar novos itens da caixa de ferramentas, dos quais você pode usar grupos de elementos ou elementos com sua própria escolha de propriedades. Para obter mais informações, consulte [definir um item da caixa de ferramentas de modelagem personalizada](../modeling/define-a-custom-modeling-toolbox-item.md).

 A figura a seguir mostra como alterar o tamanho de uma forma ou seu nome.

 ![Ajustando um elemento de modelo](../modeling/media/uml-drawadjust1.png "UML_DrawAdjust1")

> [!TIP]
> Os comandos internos não incluem um comando para alinhar formas de forma organizada. No entanto, você pode facilmente criar seu próprio comando de alinhamento copiando o código no exemplo em [exibir um modelo UML em diagramas](../modeling/display-a-uml-model-on-diagrams.md).

 A figura a seguir mostra como ajustar a rota e a posição de um conector ou seus rótulos.

 ![Ajustando um conector](../modeling/media/uml-drawadjust2.png "UML_DrawAdjust2")

#### <a name="to-move-one-end-of-a-connector-to-another-shape"></a>Para mover uma extremidade de um conector para outra forma

1. Realize um dos seguintes procedimentos:

   - Pressione **Ctrl** e mova o final.

     \- ou -

   - Clique com o botão direito do mouse no conector e clique em **reconectar**.

2. Clique no final do conector que você deseja mover.

3. Clique na forma para a qual você deseja que o conector seja movido.

#### <a name="to-change-color-or-other-properties-of-an-element-relationship-or-diagram"></a>Para alterar a cor ou outras propriedades de um elemento, relação ou diagrama

- Clique no elemento e defina os campos na janela **Propriedades** .

     Se você não puder ver a janela **Propriedades** , clique com o botão direito do mouse no elemento e clique em **Propriedades.**

#### <a name="to-zoom-in-and-out-on-a-modeling-diagram"></a>Para ampliar e reduzir em um diagrama de modelagem

- Pressione e segure a tecla **Ctrl** enquanto gira a roda do mouse.

     \- ou -

- Pressione e mantenha **Ctrl + Shift**e clique no botão esquerdo ou direito do mouse.

     \- ou -

- Na barra de ferramentas dos **designers de arquitetura** , clique no sinal de adição ( **+** ) ou de subtração ( **-** ) ou escolha um nível de zoom.

## <a name="Searching"></a>Pesquisando em um diagrama
 A função localização rápida localizará itens em um diagrama. Você deve definir **examinar:** para o **documento atual**.

#### <a name="to-search-for-text-in-a-modeling-diagram"></a>Para Pesquisar texto em um diagrama de modelagem

1. Pressione **Ctrl + F**.

     \- ou -

     No menu **Editar** , aponte para **Localizar e substituir**e clique em **localização rápida**.

    > [!NOTE]
    > Na caixa de diálogo **Localizar e substituir** , você deve deixar o campo **examinar** definido como **documento atual**. Não há suporte para as outras opções.

2. Digite o texto que você deseja localizar e clique em **Localizar próximo**.

    > [!NOTE]
    > Se o texto que você deseja localizar estiver dentro de uma forma recolhida, a forma será realçada. Expanda a forma e clique em **Localizar avançar** novamente.

## <a name="Undo"></a>Desfazendo alterações no modelo
 Você pode desfazer e refazer as alterações feitas no modelo e nos diagramas usando os comandos **Undo** e **redo** no menu **Editar** .

 **Cada projeto de modelagem tem uma única pilha de alterações.** Todas as alterações feitas no modelo e nos diagramas são mantidas nessa pilha. A pilha também inclui alterações de foco de um diagrama para outro. O comando desfazer reverte as alterações nessa pilha.

 Por exemplo, digamos que você execute essas operações: faça uma alteração em Diagrama1; alterar o foco para o diagrama 2; Altere Diagram2. Quando você desfaz alterações, a primeira ação desfazer reverte a última alteração; a próxima desfazer mudará o foco para o diagrama 1; e a terceira ação desfazer reverterá a alteração para o diagrama 1.

 **Fechar um diagrama trunca a pilha de alterações.** Se você fechar um diagrama, não poderá desfazer as alterações que executou nesse diagrama e não poderá desfazer as alterações anteriores no modelo ou em qualquer um de seus diagramas.

 **Não é possível desfazer enquanto você edita uma propriedade.** Enquanto você estiver editando uma propriedade no janela Propriedades, ou em um rótulo em um diagrama, só poderá desfazer as alterações feitas nessa propriedade. Conclua a alteração na propriedade pressionando ENTER ou cancele-a pressionando ESC. Em seguida, você poderá desfazer as alterações no modelo e nos diagramas.

 **Fechar um diagrama sem salvar pode não ter o efeito esperado.** Se você fizer algumas alterações e fechar um diagrama sem salvá-lo, suas alterações ainda serão preservadas no modelo. É recomendável fechar o modelo inteiro se você quiser fazê-lo sem salvá-lo.

## <a name="Sharing"></a>Compartilhando elementos entre diagramas
 Você pode fazer uma instância específica de um elemento de modelo aparecer mais de uma vez em seus diagramas. Isso se aplica a classes, interfaces, componentes, casos de uso e atores.

 Isso será útil se você quiser mostrar diferentes grupos de relações em diferentes diagramas. Por exemplo, em um diagrama, você pode mostrar as associações entre as classes de cliente e endereço. Em outro diagrama, você pode mostrar a classe address novamente, com sua associação à área postal.

 Você pode alterar as propriedades de um elemento de modelo, como seu nome, selecionando qualquer uma de suas exibições em qualquer diagrama ou selecionando-o no Gerenciador de modelos UML.

 Cada tipo de diagrama só pode mostrar alguns tipos de elemento de modelo. Por exemplo, você não pode mostrar um caso de uso em um diagrama de componente. Portanto, os procedimentos a seguir funcionarão apenas para algumas combinações de elementos de modelo e diagrama.

#### <a name="to-add-a-new-view-of-a-model-element-by-using-uml-model-explorer"></a>Para adicionar uma nova exibição de um elemento de modelo usando o Gerenciador de modelos UML

1. Para abrir o **Gerenciador de modelos UML**, no menu **arquitetura** , aponte para **Windows**e clique em **Gerenciador de modelos UML**.

2. Arraste o elemento Model do **Gerenciador de modelos UML** para um diagrama compatível no mesmo projeto.

     Uma forma que fornece uma exibição do elemento Model é exibida, que pode ser além das exibições em outros diagramas ou no mesmo diagrama.

    > [!NOTE]
    > O efeito é diferente quando você arrasta uma classe ou componente para um diagrama de sequência. Nesse caso, uma nova linha de vida é criada cujo tipo é a classe ou componente. Para obter mais informações, consulte [diagramas de sequência UML: diretrizes](../modeling/uml-sequence-diagrams-guidelines.md).

#### <a name="to-add-a-new-view-of-a-model-element-by-using-paste-reference"></a>Para adicionar uma nova exibição de um elemento de modelo usando colar referência

1. Clique com o botão direito do mouse em um elemento existente e clique em **copiar**.

    - Você pode copiar vários elementos ao mesmo tempo. Mantenha pressionada a tecla CTRL enquanto clica em cada elemento, clique com o botão direito do mouse em um deles e clique em **copiar**.

2. Clique com o botão direito do mouse em uma parte vazia de um diagrama compatível e clique em **colar referência**.

     É exibida outra exibição do mesmo elemento.

    > [!NOTE]
    > Isso é diferente do comando **Paste** , que cria um novo elemento no modelo. Para obter mais informações, consulte [copiando elementos e grupos de elementos relacionados](#Copying).

> [!NOTE]
> Se você adicionar a uma exibição de diagrama de dois elementos de modelo que já estão conectados por uma relação, uma visualização da relação também será exibida no diagrama. Você pode excluir essa exibição apenas removendo um dos elementos do diagrama ou excluindo a relação do modelo.

## <a name="Copying"></a>Copiando elementos e grupos de elementos relacionados
 Você pode copiar e colar elementos de modelo e pode copiar e colar grupos de elementos com as relações entre eles.

> [!NOTE]
> Os comandos de **referência** **Paste** e Paste têm efeitos diferentes. **Colar** cria novos elementos cujas propriedades são como aquelas dos elementos copiados. A **referência de colagem** cria novas exibições dos mesmos elementos.

#### <a name="to-copy-elements-and-their-relationships"></a>Para copiar elementos e suas relações

1. No diagrama com os elementos que você deseja copiar, selecione um ou mais elementos.

    > [!NOTE]
    > Você não pode copiar relações, exceto como parte de um grupo de elementos.

2. No menu **Editar** , clique em **copiar**.

3. Se você quiser copiar os elementos para outro diagrama, crie o novo diagrama ou abra o diagrama existente.

4. No menu **Editar** , clique em **colar**.

    - As cópias dos elementos são exibidas, juntamente com cópias de quaisquer relações vinculadas entre eles.

    - Cada novo elemento terá um novo nome gerado automaticamente.

5. Ajuste as posições, os nomes e outras propriedades dos novos elementos e relações.

> [!NOTE]
> Você não pode copiar um elemento de modelo de um modelo para outro, por exemplo, se você tiver dois modelos na mesma solução. Mas você pode copiar elementos de um diagrama para outro.

#### <a name="to-copy-an-entire-diagram"></a>Para copiar um diagrama inteiro

1. Crie um novo diagrama.

2. Selecione todos os elementos em um diagrama existente, copie-os e cole-os em um novo.

   Não é possível replicar um diagrama copiando e colando em Gerenciador de Soluções.

## <a name="Deleting"></a>Excluindo um elemento de modelo ou suas exibições
 Alguns tipos de elementos, especificamente classificadores, podem ser removidos de um diagrama sem excluí-los do modelo. Os classificadores são os principais elementos que são exibidos em diagramas de classe, diagramas de componente e diagramas de caso de uso. Eles podem aparecer em mais de um diagrama. Para esses tipos de elementos, há dois comandos separados: **remover do diagrama** e **excluir do modelo**.

 Por outro lado, ao excluir uma relação de um diagrama, você sempre a exclui do modelo.

> [!NOTE]
> Determinados tipos de elementos em um diagrama UML têm rótulos. Quando você seleciona esses elementos desenhando um retângulo em volta deles, é possível selecionar os rótulos, mas não os elementos que possuem esses rótulos. Não há suporte para a exclusão de um subconjunto de elementos selecionados dessa maneira. Para selecionar um subconjunto desses elementos, pressione e mantenha pressionada a tecla **Ctrl** enquanto clica em cada elemento.

#### <a name="to-remove-a-classifiers-view-from-a-diagram"></a>Para remover o modo de exibição de um classificador de um diagrama

- Clique com o botão direito do mouse no elemento no diagrama e clique em **remover do diagrama**.

  \- ou -

- Clique no elemento no diagrama e pressione a tecla **delete** .

  - Essa exibição do elemento desaparece. No entanto, o elemento permanece no modelo e você ainda pode encontrá-lo no **Gerenciador de modelos UML**. Quaisquer outras exibições do mesmo elemento também permanecem.

  - Cada conector que termina nessa forma é removido do diagrama, mas a relação que ele representa permanece no modelo. Você pode ver a relação no **Gerenciador de modelos UML** em **relações**, em cada elemento ao qual ele se conecta.

#### <a name="to-delete-an-element-from-the-model"></a>Para excluir um elemento do modelo

- Clique com o botão direito do mouse no elemento no **Gerenciador de modelos UML** ou em um diagrama e clique em **excluir do modelo**.

  - O elemento é excluído de cada diagrama no qual ele aparece.

  - Cada relação que termina nesse elemento também é excluída do modelo.

#### <a name="to-delete-a-relationship-from-the-model"></a>Para excluir uma relação do modelo

- Clique com o botão direito do mouse na relação em um diagrama ou em um **Gerenciador de modelos UML**e clique em **excluir do modelo**.

    > [!CAUTION]
    > Não é possível remover uma relação de um diagrama sem removê-la do modelo.

     A relação é excluída do modelo e é excluída de cada diagrama no qual ela aparece.

## <a name="presentation"></a>Preparando um diagrama para apresentação
 Os recursos a seguir ajudam você a chamar a atenção para partes específicas do diagrama, adicionar explicações ou dividir um diagrama em diferentes áreas de interesse.

- Você pode copiar qualquer parte de um diagrama em um Word, PowerPoint ou outro documento. Selecione as formas e os conectores desejados, clique com o botão direito do mouse e clique em **copiar**.

- A cor de qualquer forma ou conector pode ser alterada. Selecione uma ou mais formas e altere a propriedade **cor** . Se você não conseguir ver a janela **Propriedades**, pressione **F4**.

- Em diagramas de alguns tipos, você pode desenhar linhas, retângulos e elipses da seção **formas simples** da caixa de ferramentas. Essas formas não formam parte do modelo UML.

- Para rotular uma área, você pode arrastar um comentário da caixa de ferramentas e, em seguida, definir sua propriedade **transparente** como **true**. Como as formas simples, os comentários não formam parte do modelo UML e não aparecem no Gerenciador de modelos UML.

- Para adicionar observações e explicações a elementos de modelo, você pode criar comentários e vinculá-los aos elementos.

- Para alinhar de forma organizada uma coluna ou formas de linha no diagrama, você pode instalar o comando Alinhar formas. Isso está disponível como exemplo de extensão UML: [UML: comando para alinhar formas](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)

### <a name="to-export-a-diagram-as-an-image"></a>Para exportar um diagrama como uma imagem
 Para obter mais informações, consulte [exportar diagramas como imagens](../modeling/export-diagrams-as-images.md).

## <a name="extensions"></a>Estendendo os designers UML
 Você pode adicionar uma nova funcionalidade às ferramentas UML e adaptar a notação de diagrama às suas próprias necessidades. Para obter mais informações, consulte [estender modelos e diagramas UML](../modeling/extend-uml-models-and-diagrams.md).

 Há várias extensões de exemplo disponíveis. Você pode simplesmente instalá-los e usá-los ou pode usar o código-fonte como base para suas próprias extensões. Os exemplos incluem:

|||
|-|-|
|[Alinhar formas](http://code.msdn.microsoft.com/UML-command-to-Align-4139c0d7)|Comando de menu que ajuda você a organizar um diagrama.|
|[Link para docs](http://code.msdn.microsoft.com/Link-UML-elements-to-0adbf5a8)|Vincule qualquer elemento UML a títulos do Word, slides do PowerPoint, arquivos de qualquer tipo, diagramas UML ou outros elementos UML. O link pode ser feito simplesmente arrastando. Posteriormente, você pode clicar duas vezes no elemento para ver o item vinculado. Por exemplo, você pode vincular casos de uso a especificações de palavras ou diagramas de atividade detalhados e ações para slides de storyboard.|
|[Entrada rápida](http://code.msdn.microsoft.com/UML-Rapid-Entry-using-Text-0813ad8a)|Crie um modelo rapidamente usando a entrada de texto. Útil para capturar ideias em reuniões.|
|[Cor por estereótipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|As classes de cores de acordo com o estereótipo. Você pode estender facilmente o código para trabalhar com seus próprios estereótipos.|
|[Modelagem de domínio](http://code.msdn.microsoft.com/UML-Domain-Modeling-6df6f7f4)|Padrões convenientes para modelos de negócios. As associações são mostradas sem setas por padrão e as operações não aparecem em classes.|

## <a name="see-also"></a>Consulte também
 [Criar projetos de modelagem UML e diagramas](../modeling/create-uml-modeling-projects-and-diagrams.md) [analisando e modelando a arquitetura](../modeling/analyze-and-model-your-architecture.md) [criar modelos para seu aplicativo](../modeling/create-models-for-your-app.md)
