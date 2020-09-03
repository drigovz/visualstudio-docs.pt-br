---
title: Definir pacotes e namespaces | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, namespaces
- UML, namespaces
- UML, packages
- UML model, packages
ms.assetid: 79147068-02d5-4b70-933d-f647c1da3829
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 657bb91295134352fb00649ad06f59e34593c578
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669910"
---
# <a name="define-packages-and-namespaces"></a>Definir pacotes e namespaces
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, um *pacote* é um contêiner para as definições de elementos UML, como classes, casos de uso e componentes. Um pacote também pode conter outros pacotes.

 No Gerenciador de modelos UML, todas as definições dentro de um pacote são aninhadas sob o pacote. O modelo UML é um tipo de pacote e forma a raiz da árvore.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="in-this-topic"></a>Neste tópico
 [Namespaces](#Namespaces)

 [Criando e exibindo pacotes](#Packages)

 [Criando elementos de modelo dentro de pacotes](#Elements)

 [Movendo elementos para dentro ou para fora de um pacote](#Moving)

 [Colando elementos em um pacote](#Pasting)

 [Importar relações entre pacotes](#Import)

 [Referências de um namespace para outro](#References)

 [Propriedades de pacotes](#Properties)

## <a name="namespaces"></a><a name="Namespaces"></a> Namespaces
 Os pacotes são úteis para separar o trabalho em áreas diferentes. Cada pacote define um namespace para que os nomes definidos em diferentes pacotes não entrem em conflito entre si.

 A propriedade nome qualificado de cada elemento é o nome qualificado do pacote ao qual pertence, seguido pelo nome do elemento. Por exemplo, se seu pacote for chamado `MyPackage` , uma classe dentro do pacote terá um nome qualificado como `MyPackage::MyClass` . Como cada elemento está contido dentro de um modelo, cada nome qualificado começa com o nome do modelo.

 Um modelo também define um namespace, de modo que o nome qualificado de cada elemento em um modelo começa com o nome do modelo.

 Outros elementos de modelo também definem namespaces. Por exemplo, uma operação pertence ao namespace definido por sua classe pai, de modo que seu nome qualificado é como `MyModel ::MyPackage ::MyClass ::MyOperation` . Da mesma maneira, uma ação pertence ao namespace definido por sua atividade pai.

 Os pacotes são contêineres. Se você mover ou excluir um pacote, as classes, os pacotes e outras coisas definidas dentro dele também serão movidos ou excluídos. O mesmo é verdadeiro para outros elementos que definem namespaces.

## <a name="creating-and-viewing-packages"></a><a name="Packages"></a> Criando e exibindo pacotes
 Você pode criar um pacote em um diagrama de classe UML ou no Gerenciador de modelos UML.

#### <a name="to-create-a-package-in-a-uml-class-diagram"></a>Para criar um pacote em um diagrama de classes UML

1. Abra um diagrama de classe UML ou crie um novo.

2. Clique na ferramenta **pacote** .

3. Clique em qualquer lugar no diagrama. Uma nova forma de pacote será exibida.

     Você pode clicar dentro de um pacote existente para aninhar um pacote em outro.

4. Digite um novo nome para o pacote.

#### <a name="to-create-a-package-in-uml-model-explorer"></a>Para criar um pacote no Gerenciador de modelos UML

1. Abra o **Gerenciador de modelos UML**. No menu **arquitetura** , aponte para **Windows**e clique no **Gerenciador de modelos UML**.

2. Clique com o botão direito do mouse em um pacote ou modelo ao qual você deseja adicionar um novo pacote.

   > [!NOTE]
   > Você pode aninhar um pacote dentro de outro pacote.

3. Aponte para **Adicionar** e clique em **pacote**.

    Um novo pacote aparece no modelo.

4. Digite um novo nome para o pacote.

   Se você tiver criado um pacote no Gerenciador de modelos UML, poderá exibi-lo em um diagrama de classes UML. Você também pode exibir um pacote em mais de um diagrama de classes UML.

#### <a name="to-show-an-existing-package-on-a-uml-class-diagram"></a>Para mostrar um pacote existente em um diagrama de classes UML

- Arraste o pacote do Gerenciador de modelos UML para o diagrama de classe.

    > [!NOTE]
    > Isso cria uma exibição do pacote neste diagrama. Ele não mostrará, necessariamente, todos os elementos que o pacote contém. Para verificar se você vê todo o conteúdo do pacote, exiba-o no Gerenciador de modelos UML.

## <a name="creating-model-elements-inside-packages"></a><a name="Elements"></a> Criando elementos de modelo dentro de pacotes
 Há quatro maneiras pelas quais você pode posicionar elementos de modelo dentro de um pacote:

- Adicione um novo elemento a um pacote no Gerenciador de modelos UML.

- Adicione classes e outros tipos a pacotes em um diagrama de classes UML.

- Defina a propriedade **LinkedPackage** de um diagrama para que os novos elementos criados no diagrama sejam colocados dentro do pacote especificado. Diagramas de classe, diagramas de componente e diagramas de casos de uso podem ser vinculados a um pacote dessa maneira.

- Mover elementos para dentro ou para fora de um pacote no Gerenciador de modelos UML.

  Um elemento em um pacote aparece abaixo do pacote no Gerenciador de modelos UML e seu nome qualificado começa com o nome qualificado do pacote. Para ver o nome qualificado de qualquer elemento, clique com o botão direito do mouse no elemento e clique em **Propriedades**. A propriedade **nome qualificado** aparece na janela **Propriedades** .

#### <a name="to-create-an-element-in-a-package-in-uml-model-explorer"></a>Para criar um elemento em um pacote no Gerenciador de modelos UML

1. Abra o **Gerenciador de modelos UML**. No menu **Exibir** , aponte para **outras janelas**e clique em Gerenciador de **modelos UML**.

2. Clique com o botão direito do mouse em um pacote ou em um modelo ao qual você deseja adicionar um novo elemento.

3. Aponte para **Adicionar**e, em seguida, clique no tipo de elemento que você deseja adicionar.

     O novo elemento aparece abaixo do pacote.

4. Digite um nome para o novo elemento.

    > [!NOTE]
    > O novo elemento não aparece em nenhum diagrama. Para criar uma exibição do novo elemento, você pode arrastá-lo do Gerenciador de modelos UML para um diagrama. O diagrama deve ser um tipo que exibirá esse tipo de elemento.

#### <a name="to-create-an-element-in-a-package-on-a-uml-class-diagram"></a>Para criar um elemento em um pacote em um diagrama de classes UML

1. Abra um diagrama de classe no qual o pacote é exibido.

    - Crie um novo pacote, se ainda não tiver feito isso.

    - Para fazer com que um pacote existente apareça em um diagrama de classe, você pode arrastar o pacote do **Gerenciador de modelos UML** para o diagrama de classe.

2. Clique na ferramenta para uma classe, interface ou enumeração ou pacote.

3. Clique no pacote em que você deseja colocar o novo elemento.

     O novo elemento aparece dentro do pacote.

#### <a name="to-create-all-the-elements-of-a-diagram-in-a-specified-package"></a>Para criar todos os elementos de um diagrama em um pacote especificado

1. Crie o pacote, se você ainda não tiver feito isso.

2. Abra um diagrama de componente, use diagrama de caso ou diagrama de classe UML.

3. Abra as propriedades do diagrama. Clique com o botão direito do mouse em uma parte em branco do diagrama e clique em **Propriedades**.

4. Na propriedade **pacote vinculado** , escolha o pacote que você deseja que contenha o conteúdo do diagrama.

5. Crie novos elementos no diagrama. Eles serão colocados no pacote.

    - O **nome qualificado** de cada elemento será iniciado com o nome qualificado do pacote.

    - No **Gerenciador de modelos UML**, cada elemento aparecerá sob o pacote.

## <a name="moving-elements-into-and-out-of-packages"></a><a name="Moving"></a> Movendo elementos para dentro e para fora dos pacotes
 Você pode mover um ou mais elementos para dentro ou para fora de um pacote.

 Se você mover um pacote, tudo dentro dele será movido com ele.

#### <a name="to-move-an-element-into-or-out-of-a-package"></a>Para mover um elemento para dentro ou para fora de um pacote

- No Gerenciador de modelos UML, arraste o elemento para dentro ou para fora da árvore cuja raiz é o pacote.

     O nome qualificado do elemento será alterado para mostrar seu novo pacote ou modelo proprietário.

     \- ou –

- Em um diagrama de classe, arraste o elemento para uma forma de pacote.

     O nome qualificado do elemento será alterado para mostrar seu novo pacote proprietário.

    > [!NOTE]
    > Se você arrastar um elemento de um pacote para uma parte em branco do diagrama, seu pacote proprietário não será alterado. Isso permite que você crie um diagrama que mostra elementos de vários pacotes sem precisar mostrar os próprios pacotes.

## <a name="pasting-elements-into-a-package"></a><a name="Pasting"></a> Colando elementos em um pacote
 Você pode colar um elemento em um pacote. Se você colar um grupo de elementos relacionados em um pacote, as relações entre eles também serão coladas.

#### <a name="to-paste-elements-into-a-package-on-a-uml-class-diagram"></a>Para colar elementos em um pacote em um diagrama de classes UML

1. Em um diagrama de classes UML, selecione todos os elementos que você deseja copiar. Clique com o botão direito do mouse em um deles e clique em **copiar**.

2. Clique com o botão direito do mouse no pacote e clique em **colar**.

    > [!NOTE]
    > O pacote pode estar em um diagrama diferente.

## <a name="import-relationships-between-packages"></a><a name="Import"></a> Importar relações entre pacotes
 Você pode definir uma relação de importação entre pacotes, usando a ferramenta de **importação** .

 Importar significa que os elementos definidos no pacote importado, que são os elementos na extremidade da seta da relação, são efetivamente definidos também no pacote de importação. Todos os elementos cuja visibilidade é definida como **pacote** também estarão visíveis no pacote de importação.

 Evite criar loops em relações de importação.

## <a name="references-from-one-namespace-to-another"></a><a name="References"></a> Referências de um namespace para outro
 Se você quiser fazer referência a um elemento de um pacote de outro, deverá usar o nome qualificado do elemento.

 Por exemplo, suponha que o pacote `SalesCommon` defina o tipo `CustomerAddress` . Em outro pacote `RestaurantSales` , você deseja definir um tipo `MealOrder` , que tem um atributo do tipo endereço do cliente. Você tem duas opções:

- Especifique o tipo do atributo usando o nome totalmente qualificado `SalesCommon::CustomerAddress` . Você deve fazer isso somente se `CustomerAddress` o tiver sua propriedade **Visibility** definida como **Public**.

- Crie uma relação de importação do `RestaurantSales` pacote para o `SalesCommon` pacote. Em seguida, você pode usar `CustomerAddress` sem usar seu nome qualificado.

## <a name="properties-of-packages"></a><a name="Properties"></a> Propriedades de pacotes
 Cada pacote tem as seguintes propriedades. Para ver as propriedades, clique com o botão direito do mouse no pacote, em um diagrama ou em um Gerenciador de modelos UML, e clique em **Propriedades**.

|Propriedade|Valor padrão|Descrição|
|--------------|-------------------|-----------------|
|**Nome**|(um novo nome)|O nome do pacote. Você pode alterá-lo no diagrama ou na janela Propriedades.|
|**Nome Qualificado**|*Contêiner* :: *nome do pacote*|O nome completo, prefixado pelo nome do pacote ou modelo que contém este pacote. Para obter mais informações, consulte [Namespaces](#Namespaces).|
|**Perfis**|(vazio)|Uma lista dos perfis vinculados a este pacote. Esses perfis fornecem estereótipos que podem ser aplicados aos elementos dentro do pacote. Para obter mais informações, consulte [personalizar seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|
|**Visibilidade**|**Pública**|A visibilidade do pacote fora de seu pacote pai.|
|**Itens de trabalho**|(vazio)|Uma lista de itens de trabalho vinculados. Para obter mais informações, consulte [vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md).|
|**Local de definição**|(um nome)|O nome do arquivo em que os detalhes do pacote são armazenados. Os arquivos estão dentro da pasta do projeto **ModelDefinition** . Essas informações podem ser úteis para fins de controle do código-fonte.|
|**Descrição**|(vazio)|Uma descrição do pacote.|
|**Estereótipos**|(vazio)|Estereótipos que são aplicados a este pacote. A lista de estereótipos disponíveis é determinada pelos perfis que você escolheu para este pacote e os pacotes que o contêm. Para obter mais informações, consulte [personalizar seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md).|

## <a name="how-packages-are-stored"></a>Como os pacotes são armazenados
 Quando você cria um novo pacote, um novo arquivo **. Uml** é criado na pasta do projeto **ModelDefinition** . O modelo raiz, que também é um pacote, também é armazenado em um arquivo **. Uml** .

 Além disso, cada diagrama é armazenado em dois arquivos, um que representa as formas do diagrama e um arquivo **. layout** que registra as posições das formas.

## <a name="see-also"></a>Consulte Também
 [Editar modelos UML e](../modeling/edit-uml-models-and-diagrams.md) diagramas [diagramas de classes UML: referenciar](../modeling/uml-class-diagrams-reference.md) [diagramas de classe UML: diretrizes](../modeling/uml-class-diagrams-guidelines.md) [gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md)
