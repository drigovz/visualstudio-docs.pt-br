---
title: Associar controles WPF a um conjunto de dados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 80233f0786018bf1b4b18dbfa990a143d298f559
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439518"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associar controles do WPF a um conjunto de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste passo a passo, você criará um aplicativo WPF que contém controles de associação de dados. Os controles são associados a registros de produto que são encapsulados em um conjunto de dados. Você também adicionará botões para navegar pelos produtos e salvar alterações em registros de produtos.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
- Criando um aplicativo WPF e um conjunto de dados gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.  
  
- Criando um conjunto de controles de associação de dados ao arrastar uma tabela de dados da janela **Fontes de Dados** para uma janela do WPF Designer.  
  
- Criando botões que navegam para a frente e para trás nos registros de produtos.  
  
- Criando um botão para salvar as alterações que os usuários fazem nos registros de produtos na tabela de dados e na fonte de dados subjacente.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele. Você pode baixar o banco de dados AdventureWorksLT a [site da CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:  
  
- Conjuntos de dados e TableAdapters. Para obter mais informações, consulte [ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
- Trabalhando com o WPF Designer. Para obter mais informações, consulte [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Associação de dados do WPF. Para obter mais informações, consulte [Visão geral de vinculação de dados](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-project"></a>Criar o projeto  
 Crie um novo projeto WPF. O projeto exibirá registros de produtos.  
  
#### <a name="to-create-the-project"></a>Para criar o projeto  
  
1. Inicie o Visual Studio.  
  
2. No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3. Expanda **Visual Basic** ou **Visual C#** e selecione **Windows**.  
  
4. Selecione o modelo de projeto **Aplicativo WPF**.  
  
5. No **nome** , digite `AdventureWorksProductsEditor` e clique em **Okey**.  
  
     O Visual Studio cria o `AdventureWorksProductsEditor` projeto.  
  
## <a name="create-a-dataset-for-the-application"></a>Criar um conjunto de dados para o aplicativo  
 Antes de criar controles de associação de dados, você deve definir um modelo de dados para seu aplicativo e adicioná-lo à janela **Fontes de Dados**. Neste passo a passo, você criará um conjunto de dados para usar como modelo de dados.  
  
#### <a name="to-create-a-dataset"></a>Para criar um conjunto de dados  
  
1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
     A janela **Fontes de Dados** é aberta.  
  
2. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     O **Assistente de Configuração de Fonte de Dados** é aberto.  
  
3. Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Avançar**.  
  
4. Na página **Escolher um Modelo de Banco de Dados**, selecione **Conjunto de Dados** e clique em **Avançar**.  
  
5. Na página **Escolha a Conexão de Dados**, selecione uma das seguintes opções:  
  
    - Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione-a e clique em **Avançar**.  
  
    - Clique em **Nova Conexão** e crie uma conexão com o banco de dados AdventureWorksLT.  
  
6. Na página **Salvar a Cadeia de Conexão no Arquivo de Configuração do Aplicativo** marque a caixa de seleção **Sim, salvar a conexão como** e clique em **Próximo**.  
  
7. Na página **Escolher Objetos do Banco de Dados**, expanda **Tabelas** e selecione a tabela **Produto (SalesLT)**.  
  
8. Clique em **Finalizar**.  
  
     Visual Studio adiciona um novo arquivo Adventureworksltdataset XSD ao projeto e ele adiciona um correspondente **AdventureWorksLTDataSet** de item para o **fontes de dados** janela. O arquivo AdventureWorksLTDataSet.xsd define um conjunto de dados tipado nomeado `AdventureWorksLTDataSet` e um TableAdapter nomeado `ProductTableAdapter`. A seguir neste passo a passo, você usará o `ProductTableAdapter` para preencher o conjunto de dados com dados e salvar as alterações no banco de dados.  
  
9. Compile o projeto.  
  
## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Editar o método de preenchimento padrão do TableAdapter  
 Para preencher o conjunto de dados com dados, use o método `Fill` do `ProductTableAdapter`. Por padrão, o método `Fill` preenche o `ProductDataTable` no `AdventureWorksLTDataSet` com todas as linhas de dados da tabela Produto. Você pode modificar esse método para retornar apenas um subconjunto das linhas. Para este passo a passo, modifique o método `Fill` para retornar somente linhas de produtos com fotos.  
  
#### <a name="to-load-product-rows-that-have-photos"></a>Para carregar as linhas de produtos que possuem fotos  
  
1. Na **Gerenciador de soluções**, duas vezes no arquivo Adventureworksltdataset.  
  
     O designer de conjunto de dados é aberto.  
  
2. No designer, clique com botão direito do **Fill,GetData()** de consulta e selecione **configurar**.  
  
     O assistente **Configuração do TableAdapter** é aberto.  
  
3. Na página **Insira uma Instrução SQL**, adicione a seguinte cláusula WHERE após a instrução `SELECT` na caixa de texto.  
  
    ```  
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'  
    ```  
  
4. Clique em **Finalizar**.  
  
## <a name="define-the-user-interface"></a>Definir a interface do usuário  
 Adicione vários botões à janela, modificando o XAML no WPF Designer. A seguir neste passo a passo, você adicionará o código que permite aos usuários navegar e salvar alterações nos registros de produtos, usando esses botões.  
  
#### <a name="to-define-the-user-interface-of-the-window"></a>Para definir a interface do usuário da janela  
  
1. Na **Gerenciador de soluções**, clique duas vezes em MainWindow. XAML.  
  
     A janela é aberta no WPF Designer.  
  
2. Na exibição [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="625" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3. Compile o projeto.  
  
## <a name="createdata-bound-controls"></a>Controles associados a criar  
 Crie controles que exibem registros do cliente, arrastando o `Product` tabela do **fontes de dados** janela para o WPF Designer.  
  
#### <a name="to-create-data-bound-controls"></a>Para adicionar controles de associação de dados  
  
1. Na janela **Fontes de Dados**, abra o menu suspenso para o nó **Produto** e selecione **Detalhes**.  
  
2. Expanda o nó **Produto**.  
  
3. Neste exemplo, alguns campos não serão exibidos, portanto, clique no menu suspenso ao lado dos seguintes nós e selecione **Nenhum**:  
  
    - ProductCategoryID  
  
    - ProductModelID  
  
    - ThumbnailPhotoFileName  
  
    - rowguid  
  
    - ModifiedDate  
  
4. Clique no menu suspenso ao lado do nó **ThumbNailPhoto** e selecione **Imagem**.  
  
    > [!NOTE]
    > Por padrão, todos os itens na janela **Fontes de Dados** que representam as imagens têm seu controle padrão definido como **Nenhum**. Isso ocorre porque as imagens são armazenadas como matrizes de bytes em bancos de dados e as matrizes de bytes podem conter qualquer coisa, desde uma simples matriz de bytes até um arquivo executável de um aplicativo grande.  
  
5. Na janela **Fontes de Dados**, arraste o nó **Produto** para a linha de grade sob a linha que contém os botões.  
  
     O Visual Studio gera XAML que define um conjunto de controles associados aos dados na tabela **Produtos**. Também gera um código que carrega os dados. Para obter mais informações sobre o XAML e o código gerado, consulte [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6. No designer, clique na caixa de texto ao lado do rótulo de **ID do Produto**.  
  
7. Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.  
  
## <a name="navigating-product-records"></a>Navegando nos registros de produto  
 Adicione o código que permite aos usuários rolar nos registros do produto ao usar os botões **\<** e **>**.  
  
#### <a name="to-enable-users-to-navigate-product-records"></a>Para permitir que os usuários naveguem nos registros do produto  
  
1. No designer, clique duas vezes no botão **<** na superfície da janela.  
  
     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `backButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2. Modifique o manipulador de eventos `Window_Loaded` para que `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` fiquem fora do método e acessíveis a todo o formulário. Declare apenas esses globais para o formulário e atribuí-los dentro de `Window_Loaded` manipulador de eventos semelhante à seguinte:  
  
     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]  
  
3. Adicione o seguinte código ao manipulador de eventos do `backButton_Click`:  
  
     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]  
  
4. Retorne ao designer e clique duas vezes no botão **>**.  
  
5. Adicione o seguinte código ao manipulador de eventos do `nextButton_Click`:  
  
     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]  
  
## <a name="savechanges-to-product-records"></a>Salvar alterações em registros de produtos  
 Adicione o código que permite aos usuários salvar alterações em registros de produtos ao usar o botão **Salvar alterações**.  
  
#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>Para adicionar a capacidade de salvar as alterações em registros de produtos  
  
1. No designer, clique duas vezes no botão **Salvar alterações**.  
  
     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `saveButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2. Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`:  
  
     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]  
  
    > [!NOTE]
    > Este exemplo usa o método `Save` do `TableAdapter` para salvar as alterações. Isso ocorre neste passo a passo, porque apenas uma tabela de dados está sendo alterada. Se for necessário salvar alterações em várias tabelas de dados, você pode também usar o método `UpdateAll` do `TableAdapterManager` que o Visual Studio gera com o seu conjunto de dados. Para obter mais informações, consulte [visão geral de TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650).  
  
## <a name="test-the-application"></a>Testar o aplicativo  
 Crie e execute o aplicativo. Verifique se você pode exibir e atualizar registros de produtos.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1. Pressione **F5**.  
  
     O aplicativo é compilado e executado. Verifique o seguinte:  
  
    - As caixas de texto exibem dados do primeiro registro do produto que tem uma foto. Este produto tem a ID 713 e o nome **Long-Sleeve Logo Jersey, S**.  
  
    - Você pode clicar nos botões **>** ou **<** para navegar em outros registros de produto.  
  
2. Em um dos registros de produto, altere o valor **Tamanho** e clique em **Salvar Alterações**.  
  
3. Feche o aplicativo e reinicie-o pressionando **F5** no Visual Studio.  
  
4. Navegue até o registro do produto que você alterou e verifique se a mudança persistiu.  
  
5. Feche o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Depois de completar este passo a passo, você poderá realizar as seguintes tarefas relacionadas:  
  
- Saiba como usar a janela **Fontes de Dados** no Visual Studio para associar controles do WPF a outros tipos de fontes de dados. Para obter mais informações, consulte [controles de WPF associar a um WCF data service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).  
  
- Saiba como usar a janela **Fontes de Dados** no Visual Studio para exibir dados relacionados (isto é, dados em uma relação pai-filho) em controles do WPF. Para obter mais informações, confira [Passo a passo: Exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Visão de geral do Designer do Silverlight e WPF](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Visão geral da vinculação de dados](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
