---
title: Associar controles do WPF a um conjunto de dados
description: Crie um aplicativo WPF no Visual Studio que contém controles vinculados a dados, que são associados a registros de produtos que são encapsulados em um DataSet.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 2ebfc2071bdf9f9e9dc40b36744bb34d4a68ac04
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859275"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>Associar controles do WPF a um conjunto de dados

Neste tutorial, você cria um aplicativo do WPF que contém controles associados a dados. Os controles são associados a registros de produto que são encapsulados em um conjunto de dados. Você também adiciona botões para navegar pelos produtos e salvar alterações em registros de produtos.

Este passo a passo ilustra as seguintes tarefas:

- Criando um aplicativo WPF e um conjunto de dados gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.

- Criando um conjunto de controles de associação de dados ao arrastar uma tabela de dados da janela **Fontes de Dados** para uma janela do WPF Designer.

- Criando botões que navegam para a frente e para trás nos registros de produtos.

- Criando um botão para salvar as alterações que os usuários fazem nos registros de produtos na tabela de dados e na fonte de dados subjacente.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>Pré-requisitos

Você precisará dos seguintes componentes para concluir este passo a passo:

- Visual Studio

- Acesso a uma instância em execução do SQL Server ou SQL Server Express que tem o banco de dados de exemplo AdventureWorks Light (AdventureWorksLT) anexado a ele. Você pode baixar o banco de dados AdventureWorksLT do [arquivo CodePlex](https://archive.codeplex.com/?p=awlt2008dbscript).

Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:

- Conjuntos de dados e TableAdapters. Para obter mais informações, consulte [ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md) e [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

- Associação de dados do WPF. Para obter mais informações, consulte [visão geral da ligação de dados](/dotnet/desktop-wpf/data/data-binding-overview).

## <a name="create-the-project"></a>Criar o projeto

Crie um novo projeto do WPF para exibir registros de produto.

::: moniker range="vs-2017"

1. Abra o Visual Studio.

2. No menu **arquivo** , selecione **novo** > **projeto**.

3. Expanda **Visual Basic** ou **Visual C#** e selecione **Windows**.

4. Selecione o modelo de projeto de **aplicativo do WPF** .

5. Na caixa **nome** , digite **AdventureWorksProductsEditor** e, em seguida, selecione **OK**.

::: moniker-end

::: moniker range=">=vs-2019"

1. Abra o Visual Studio.

2. Na janela iniciar, escolha **criar um novo projeto**.

3. Pesquise o modelo de projeto do **aplicativo WPF** em C# e siga as etapas para criar o projeto, nomeando o projeto **AdventureWorksProductsEditor**.

::: moniker-end

   O Visual Studio cria o projeto AdventureWorksProductsEditor.

## <a name="create-a-dataset-for-the-application"></a>Criar um conjunto de um DataSet para o aplicativo

Antes de criar controles de associação de dados, você deve definir um modelo de dados para seu aplicativo e adicioná-lo à janela **Fontes de Dados**. Neste passo a passo, você criará um conjunto de dados para usar como modelo de dados.

1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

   A janela **Fontes de Dados** é aberta.

2. Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.

   O assistente de **configuração de fonte de dados** é aberto.

3. Na página **Escolher um Tipo de Fonte de Dados**, selecione **Banco de Dados** e clique em **Avançar**.

4. Na página **Escolher um Modelo de Banco de Dados**, selecione **Conjunto de Dados** e clique em **Avançar**.

5. Na página **Escolha a Conexão de Dados**, selecione uma das seguintes opções:

   - Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione-a e clique em **Avançar**.

   - Clique em **Nova Conexão** e crie uma conexão com o banco de dados AdventureWorksLT.

6. Na página **Salvar a Cadeia de Conexão no Arquivo de Configuração do Aplicativo** marque a caixa de seleção **Sim, salvar a conexão como** e clique em **Próximo**.

7. Na página **Escolher Objetos do Banco de Dados**, expanda **Tabelas** e selecione a tabela **Produto (SalesLT)**.

8. Clique em **Concluir**.

   O Visual Studio adiciona um novo `AdventureWorksLTDataSet.xsd` arquivo ao projeto e adiciona um item **AdventureWorksLTDataSet** correspondente à janela fontes de **dados** . O `AdventureWorksLTDataSet.xsd` arquivo define um dataset tipado chamado `AdventureWorksLTDataSet` e um TableAdapter chamado `ProductTableAdapter` . A seguir neste passo a passo, você usará o `ProductTableAdapter` para preencher o conjunto de dados com dados e salvar as alterações no banco de dados.

9. Compile o projeto.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>Editar o método Fill padrão do TableAdapter

Para preencher o conjunto de dados com dados, use o método `Fill` do `ProductTableAdapter`. Por padrão, o método `Fill` preenche o `ProductDataTable` no `AdventureWorksLTDataSet` com todas as linhas de dados da tabela Produto. Você pode modificar esse método para retornar apenas um subconjunto das linhas. Para este passo a passo, modifique o método `Fill` para retornar somente linhas de produtos com fotos.

1. No **Gerenciador de Soluções**, clique duas vezes no arquivo *AdventureWorksLTDataSet.xsd*.

     O designer de conjunto de dados é aberto.

2. No designer, clique com o botão direito do mouse na consulta **Fill**,**GetData()** e selecione **Configurar**.

     O assistente **Configuração do TableAdapter** é aberto.

3. Na página **Insira uma Instrução SQL**, adicione a seguinte cláusula WHERE após a instrução `SELECT` na caixa de texto.

    ```sql
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. Clique em **Concluir**.

## <a name="define-the-user-interface"></a>Definir a interface do usuário

Adicione vários botões à janela, modificando o XAML no WPF Designer. A seguir neste passo a passo, você adicionará o código que permite aos usuários navegar e salvar alterações nos registros de produtos, usando esses botões.

1. No **Gerenciador de Soluções**, clique duas vezes em *MainWindow.xaml*.

    A janela é aberta no **designer do WPF**.

2. Na exibição [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="625" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75">&lt;</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">&gt;</Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. Compile o projeto.

## <a name="create-data-bound-controls"></a>Criar controles vinculados a dados

Crie controles que exibam os registros do cliente arrastando a `Product` tabela da janela **fontes de dados** para o designer do WPF.

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

     O Visual Studio gera XAML que define um conjunto de controles associados aos dados na tabela **Produtos**. Também gera um código que carrega os dados. Para obter mais informações sobre o XAML e o código gerados, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. No designer, clique na caixa de texto ao lado do rótulo de **ID do Produto**.

7. Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.

## <a name="navigate-product-records"></a>Navegar pelos registros de produtos

Adicione o código que permite aos usuários rolar por meio de registros de produto usando os **\<** and **>** botões.

1. No designer, clique duas vezes no **<** botão na superfície da janela.

     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `backButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Modifique o manipulador de eventos `Window_Loaded` para que `ProductViewSource`, `AdventureWorksLTDataSet` e `AdventureWorksLTDataSetProductTableAdapter` fiquem fora do método e acessíveis a todo o formulário. Declare apenas que eles sejam globais para o formulário e atribua-os no `Window_Loaded` manipulador de eventos semelhante ao seguinte:

     [!code-csharp[Data_WPFDATASET#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_1.cs)]
     [!code-vb[Data_WPFDATASET#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_1.vb)]

3. Adicione o seguinte código ao manipulador de eventos do `backButton_Click`:

     [!code-csharp[Data_WPFDATASET#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_2.cs)]
     [!code-vb[Data_WPFDATASET#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_2.vb)]

4. Retorne ao designer e clique duas vezes no **>** botão.

5. Adicione o seguinte código ao manipulador de eventos do `nextButton_Click`:

     [!code-csharp[Data_WPFDATASET#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_3.cs)]
     [!code-vb[Data_WPFDATASET#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_3.vb)]

## <a name="save-changes-to-product-records"></a>Salvar alterações em registros de produtos

Adicione o código que permite aos usuários salvar alterações em registros de produtos ao usar o botão **Salvar alterações**.

1. No designer, clique duas vezes no botão **Salvar alterações**.

     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `saveButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.

2. Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`:

     [!code-csharp[Data_WPFDATASET#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-dataset_4.cs)]
     [!code-vb[Data_WPFDATASET#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-dataset_4.vb)]

    > [!NOTE]
    > Este exemplo usa o método `Save` do `TableAdapter` para salvar as alterações. Isso ocorre neste passo a passo, porque apenas uma tabela de dados está sendo alterada. Se for necessário salvar alterações em várias tabelas de dados, você pode também usar o método `UpdateAll` do `TableAdapterManager` que o Visual Studio gera com o seu conjunto de dados. Para obter mais informações, consulte [TableAdapters](../data-tools/create-and-configure-tableadapters.md).

## <a name="test-the-application"></a>Testar o aplicativo

Crie e execute o aplicativo. Verifique se você pode exibir e atualizar registros de produtos.

1. Pressione **F5**.

     O aplicativo é compilado e executado. Verifique o seguinte:

    - As caixas de texto exibem dados do primeiro registro do produto que tem uma foto. Este produto tem a ID 713 e o nome **Long-Sleeve Logo Jersey, S**.

    - Você pode clicar nos **>** **<** botões ou para navegar por outros registros de produto.

2. Em um dos registros de produto, altere o valor **Tamanho** e clique em **Salvar Alterações**.

3. Feche o aplicativo e reinicie-o pressionando **F5** no Visual Studio.

4. Navegue até o registro do produto que você alterou e verifique se a mudança persistiu.

5. Feche o aplicativo.

## <a name="next-steps"></a>Próximas etapas

Depois de concluir este passo a passos, você pode tentar as seguintes tarefas relacionadas:

- Saiba como usar a janela **Fontes de Dados** no Visual Studio para associar controles do WPF a outros tipos de fontes de dados. Para obter mais informações, consulte [associar controles WPF a um serviço de dados WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md).

- Saiba como usar a janela **Fontes de Dados** no Visual Studio para exibir dados relacionados (isto é, dados em uma relação pai-filho) em controles do WPF. Para obter mais informações, consulte [Walkthrough: exibir dados relacionados em um aplicativo do WPF](../data-tools/display-related-data-in-wpf-applications.md).

## <a name="see-also"></a>Confira também

- [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Visão geral da ligação de dados](/dotnet/desktop-wpf/data/data-binding-overview)
