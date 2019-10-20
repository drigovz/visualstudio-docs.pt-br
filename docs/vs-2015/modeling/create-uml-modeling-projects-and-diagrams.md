---
title: Criar diagramas e projetos de modelagem UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.addnewdiagramdialog
- vs.teamarch.createnewmodelingprojectdialog
helpviewer_keywords:
- projects [Visual Studio ALM], modeling
- diagrams - modeling, modeling
- modeling diagrams
- projects, UML
- UML, deleting diagrams
- UML
- UML diagrams, adding
- UML, projects
- Visual Studio ALM, modeling projects
- modeling projects
- UML diagrams
- projects, modeling
ms.assetid: c178b04b-4fd2-4bed-97e3-d793dae8649c
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0e65f2f33d9c7b034da6b58f32280c95a96bacd7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651250"
---
# <a name="create-uml-modeling-projects-and-diagrams"></a>Criar projetos e diagramas de modelagem UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os modelos UML ajudam você a entender, discutir e criar sistemas de software. O Visual Studio fornece modelos para cinco dos diagramas UML usados com mais frequência: atividade, classe, componente, sequência e caso de uso. Além disso, você pode criar diagramas de camada, que ajudam a definir a estrutura do seu sistema.

 Diagramas de modelagem UML e diagramas de camada só podem existir dentro de um projeto de modelagem. Cada projeto de modelagem contém um modelo UML compartilhado e vários diagramas UML. Cada diagrama é uma exibição parcial do modelo. O modelo UML contém todos os elementos nos diagramas UML e pode ser exibido usando o Gerenciador de modelos UML. Para obter informações sobre modelos e sua relação com diagramas, consulte [Editar diagramas e modelos UML](../modeling/edit-uml-models-and-diagrams.md). Para obter informações sobre como modelar projetos sob controle de versão, consulte [gerenciar modelos e diagramas sob controle de versão](../modeling/manage-models-and-diagrams-under-version-control.md) e [estruturar sua solução de modelagem](../modeling/structure-your-modeling-solution.md)

> [!NOTE]
> Há outro tipo de diagrama, o diagrama de classes do .NET, que é usado para visualizar o código do programa. Para obter mais informações, consulte [projetando e exibindo classes e tipos](http://go.microsoft.com/fwlink/?LinkId=142231).

## <a name="CreatingModelingDiagrams"></a>Criar um diagrama em um projeto de modelagem
 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

#### <a name="to-create-a-diagram-and-add-it-to-a-project"></a>Para criar um diagrama e adicioná-lo a um projeto

1. No menu **arquitetura** , escolha **novo UML ou diagrama de camada**.

2. Na caixa de diálogo **Adicionar novo diagrama** , clique no tipo de diagrama de modelagem desejado.

    ![Caixa de diálogo Adicionar novo diagrama](../modeling/media/uml-adddiagram.png "UML_AddDiagram")

3. Digite um nome para o novo diagrama.

4. Na caixa **Adicionar ao projeto de modelagem** :

   - Selecione um projeto de modelagem que já exista em sua solução e clique em **OK**.

     \- ou -

   1. Selecione **criar um novo projeto de modelagem**e clique em **OK**.

   2. Na caixa de diálogo **criar novo projeto de modelagem** , digite um nome e um local para o novo projeto e clique em **OK**.

        ![Caixa de diálogo Criar novo projeto de modelagem](../modeling/media/uml-createmodel.png "UML_CreateModel")

        Se sua solução estiver aberta, o novo projeto será adicionado à solução. Se você não tiver uma solução aberta, poderá digitar um nome para uma nova solução.

   Se você já tiver um projeto de modelagem, também poderá usar o procedimento a seguir.

#### <a name="to-add-a-diagram-to-an-existing-modeling-project"></a>Para adicionar um diagrama a um projeto de modelagem existente

1. Em **Gerenciador de soluções**, clique no nó projeto de modelagem.

    > [!NOTE]
    > O projeto de modelagem contém uma pasta de definição de modelo chamada **ModelDefinition**.

2. No menu **Projeto**, clique em **Adicionar Novo Item**.

3. Na caixa de diálogo **Adicionar novo item-** *\<project nome >* , em **modelos**, clique no tipo de diagrama de modelagem, por exemplo, **diagrama de componente UML**.

4. Digite um nome para o diagrama e clique em **Adicionar**.

     O diagrama de modelagem é aberto e aparece no projeto de modelagem.

    > [!CAUTION]
    > Não adicione, copie ou arraste arquivos de diagrama existentes para outros projetos de modelagem ou para outros locais na solução. Isso faz com que os elementos desapareçam dos diagramas copiados ou que ocorrem erros quando você abre os diagramas. Você deve abrir o arquivo de diagrama do projeto de modelagem no qual ele foi criado. Isso ocorre porque um diagrama UML é uma exibição do modelo que pertence ao seu projeto de modelagem. Para copiar um arquivo de diagrama, crie um novo diagrama e, em seguida, copie os elementos do diagrama de origem para o novo diagrama. Para obter mais informações, consulte [solução de problemas de projetos e diagramas de modelagem](#TroubleshootingModelingProjects).

#### <a name="to-create-a-blank-modeling-project"></a>Para criar um projeto de modelagem em branco

1. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.

2. Na caixa de diálogo **novo projeto** , em **modelos instalados**, clique em **modelagem de projetos**.

3. Na janela central, clique em **projeto de modelagem**.

4. Nomeie o projeto e especifique um local nas caixas **nome** e **local** .

5. Na caixa **solução** , selecione **Adicionar à solução** para adicionar o novo projeto a uma solução que você já abriu; ou **crie uma nova solução** para fechar qualquer solução aberta e adicionar o projeto a uma nova solução.

## <a name="RemovingModelingDiagrams"></a>Removendo diagramas de modelagem de um projeto
 Você pode excluir um diagrama permanentemente ou pode excluir temporariamente um diagrama de um projeto e, em seguida, restaurá-lo.

#### <a name="to-permanently-delete-a-diagram-from-a-project"></a>Para excluir permanentemente um diagrama de um projeto

- Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo principal que representa o diagrama e clique em **excluir**.

     O diagrama é removido do projeto e do sistema de arquivos. Os elementos mostrados no diagrama não são removidos do **Gerenciador de modelos UML**.

    > [!NOTE]
    > Cada diagrama tem dois arquivos, uma subsidiária para o outro. Por exemplo, se você tiver um diagrama de componente com o nome `CD1`, deverá excluir o arquivo chamado `CD1.componentdiagram`. Seu arquivo de subsidiária chamado `CD1.componentdiagram.layout` será excluído automaticamente.

#### <a name="to-temporarily-exclude-a-diagram-from-a-project"></a>Para excluir temporariamente um diagrama de um projeto

- Em **Gerenciador de soluções**, clique com o botão direito do mouse no arquivo de diagrama e clique em **excluir do projeto**.

     O diagrama é removido do projeto. Ele não é removido do sistema de arquivos.

    > [!NOTE]
    > Os elementos mostrados no diagrama não são removidos do **Gerenciador de modelos UML**.

#### <a name="to-restore-a-temporarily-excluded-diagram-to-a-project"></a>Para restaurar um diagrama temporariamente excluído para um projeto

1. Em **Gerenciador de soluções**, clique no nó projeto de modelagem.

    > [!NOTE]
    > O projeto de modelagem contém uma pasta de definição de modelo chamada **ModelDefinition**.

2. No menu **projeto** , clique em **Adicionar item existente**.

3. Na caixa de diálogo **Adicionar item existente** , localize o arquivo de diagrama, selecione o arquivo e clique em **Adicionar**.

     O diagrama de modelagem é aberto e aparece no projeto de modelagem.

    > [!NOTE]
    > Cada diagrama tem um par de arquivos no sistema de arquivos. Não selecione um arquivo que tenha a extensão `.layout`. Além disso, o Visual Studio não oferece suporte à adição de diagramas UML existentes a vários projetos de modelagem. Cada arquivo de diagrama deve ser aberto dentro do projeto de modelagem no qual foi criado. Isso ocorre porque um diagrama UML mostra uma exibição de um modelo que pertence a seu projeto de modelagem.

## <a name="NonModelDiagrams"></a>Diagramas que não exigem projetos de modelagem
 Os seguintes tipos de diagramas não fazem parte de um projeto de modelagem:

- Diagramas de classe criados como exibições do código-fonte. Eles não estão relacionados a diagramas de classe UML. Para obter mais informações, consulte [projetando e exibindo classes e tipos](../ide/designing-and-viewing-classes-and-types.md).

- Mapas de código. Consulte [mapear dependências em suas soluções](../modeling/map-dependencies-across-your-solutions.md).

- Diagramas que não são diagramas UML ou diagramas de camada, como linguagens específicas de domínio.

## <a name="TroubleshootingModelingProjects"></a>Solucionando problemas de projetos e diagramas de modelagem
 A tabela a seguir descreve os problemas que podem ocorrer com a modelagem de projetos ou diagramas e como resolvê-los:

|**Lo**|**Com**|**Resolução**|
|---------------|----------------|--------------------|
|O projeto de modelagem não pode ser aberto ou carregado na solução.<br /><br /> A seguinte mensagem é exibida:<br /><br /> "Um ou mais projetos na solução não foram carregados corretamente. Consulte a Janela de Saída para obter detalhes. "<br /><br /> A janela saída exibe a seguinte mensagem:<br /><br /> "*ModelingProjectFilenameAndPath*. modelproj: erro: formato de GUID não reconhecido."|Um projeto de modelagem tem referências a projetos que têm o mesmo nome e estão na mesma solução.<br /><br /> Por exemplo, uma camada é vinculada a projetos que têm o mesmo nome e estão na mesma solução.|Use um editor de texto para abrir o arquivo de projeto de modelagem, remova as referências e tente abrir o projeto de modelagem novamente.<br /><br /> Para evitar esse problema, não adicione referências a projetos que tenham o mesmo nome. Verifique se os projetos têm nomes exclusivos.|
|Os elementos estão ausentes de diagramas que são adicionados, copiados ou arrastados para outros projetos de modelagem ou para outros locais na solução.<br /><br /> - ou -<br /><br /> As seguintes mensagens são exibidas quando você tenta abrir um diagrama:<br /><br /> -"Algumas formas ou conectores no diagrama estão ausentes porque suas definições não existem neste projeto. As definições foram excluídas do modelo enquanto o diagrama foi fechado ou o diagrama foi copiado para outro projeto que não contém essas definições. "<br /><br /> - ou -<br /><br /> -"Este documento está aberto por outro projeto".|O arquivo de diagrama foi adicionado, arrastado ou copiado de um projeto de modelagem para outro projeto de modelagem ou para outro local na solução.|Para copiar um arquivo de diagrama, crie um novo diagrama e, em seguida, copie os elementos do diagrama de origem para o novo diagrama.|

## <a name="see-also"></a>Consulte também
 [Editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md) [estrutura sua solução de modelagem](../modeling/structure-your-modeling-solution.md)
