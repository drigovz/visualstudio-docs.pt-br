---
title: Associar controles WPF a um WCF data service | Microsoft Docs
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
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
caps.latest.revision: 44
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 86c4358179b86031652cf933823c00a68526e9c5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925283"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>Associar controles do WPF a um WCF Data Service
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Neste passo a passo, você criará um aplicativo WPF que contém controles de associação de dados. Os controles estão associados a registros de clientes que são encapsulados em um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)]. Você também adicionará botões que os clientes podem usar para exibir e atualizar registros.  
  
 Esta explicação passo a passo ilustra as seguintes tarefas:  
  
- Criando um Modelo de Dados de Entidade que é gerado a partir de dados no banco de dados de exemplo AdventureWorksLT.  
  
- Criando um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] que expõe os dados no modelo de dados de entidade para um aplicativo WPF.  
  
- Criando um conjunto de controles de associação de dados ao arrastar itens da janela **Fontes de Dados** para o WPF Designer.  
  
- Criando botões que navegam para a frente e para trás nos registros de clientes.  
  
- Criando um botão que salva as alterações aos dados nos controles para o [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] e fonte de dados subjacente.  
  
   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]  
  
- Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele. Você pode baixar o banco de dados AdventureWorksLT a [site da CodePlex](http://go.microsoft.com/fwlink/?linkid=87843).  
  
  Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:  
  
- WCF Data Services. Para obter mais informações, consulte [visão geral](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb).  
  
- Modelos de dados no [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)].  
  
- Modelos de Dados de Entidade e o ADO.NET Entity Framework. Para obter mais informações, consulte [visão geral do Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
- Trabalhando com o WPF Designer. Para obter mais informações, consulte [WPF e Silverlight Designer Overview](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).  
  
- Associação de dados do WPF. Para obter mais informações, consulte [Visão geral de vinculação de dados](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).  
  
## <a name="create-the-service-project"></a>Criar o projeto de serviço  
 Comece este passo a passo criando um projeto para um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
#### <a name="to-create-the-service-project"></a>Para criar o projeto de serviço  
  
1.  Inicie o Visual Studio.  
  
2.  No menu **Arquivo**, aponte para **Novo** e clique em **Projeto**.  
  
3.  Expanda **Visual C#** ou **Visual Basic** e selecione **Web**.  
  
4.  Selecione o modelo de projeto **Aplicativo Web ASP.NET**.  
  
5.  No **nome** , digite `AdventureWorksService` e clique em **Okey**.  
  
     O Visual Studio cria o `AdventureWorksService` projeto.  
  
6.  No **Gerenciador de Soluções**, clique com o botão direito do mouse em **Default.aspx** e selecione **Excluir**. Este arquivo não é necessário neste passo a passo.  
  
## <a name="create-an-entity-data-model-for-the-service"></a>Criar um modelo de dados de entidade para o serviço  
 Para expor os dados para um aplicativo usando um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], você deve definir um modelo de dados para o serviço. O [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] dá suporte a dois tipos de modelos de dados: Modelos de dados de entidade e modelos de dados personalizados que são definidos usando objetos common language runtime (CLR) que implementam o <xref:System.Linq.IQueryable%601> interface. Neste passo a passo, você criará um Modelo de Dados de Entidade para o modelo de dados.  
  
#### <a name="to-create-an-entity-data-model"></a>Para criar um Modelo de Dados de Entidade  
  
1.  No menu **Projeto**, clique em **Adicionar Novo Item**.  
  
2.  Na lista Modelos Instalados, clique em **Dados** e selecione o item do projeto **Modelo de Dados de Entidade ADO.NET**.  
  
3.  Altere o nome para `AdventureWorksModel.edmx`e clique em **Add**.  
  
     O **Assistente do Modelo de Dados de Entidade** será aberto.  
  
4.  Na página **Escolher Conteúdo do Modelo**, clique em **Gerar do banco de dados** e em **Avançar**.  
  
5.  Na página **Escolha a Conexão de Dados**, selecione uma das seguintes opções:  
  
    -   Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione-a.  
  
    -   Clique em **Nova Conexão** e crie uma conexão com o banco de dados AdventureWorksLT.  
  
6.  Na página **Escolha a Conexão de Dados**, verifique se a opção **Salvar configurações de conexão de entidade em App.Config como** está selecionada e clique em **Próximo**.  
  
7.  Na página **Escolher Objetos do Banco de Dados**, expanda **Tabelas** e selecione a tabela **SalesOrderHeader**.  
  
8.  Clique em **Finalizar**.  
  
## <a name="create-the-service"></a>Criar o serviço  
 Criar um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] para expor os dados no modelo de dados de entidade para um aplicativo WPF.  
  
#### <a name="to-create-the-service"></a>Para criar o serviço  
  
1.  No menu **Projeto**, selecione **Adicionar Novo Item**.  
  
2.  Na lista de modelos instalados, clique em **Web**e, em seguida, selecione o **WCF Data Service** item de projeto.  
  
3.  No **nome** , digite `AdventureWorksService.svc`e clique em **Add**.  
  
     O Visual Studio adiciona o `AdventureWorksService.svc` ao projeto.  
  
## <a name="configure-the-service"></a>Configurar o serviço  
 Você deve configurar o serviço para operar no Modelo de Dados de Entidades que você criou.  
  
#### <a name="to-configure-the-service"></a>Para configurar o serviço  
  
1.  No `AdventureWorks.svc` arquivo de código, substitua o `AdventureWorksService` declaração com o seguinte código de classe.  
  
     [!code-csharp[Data_WPFWCF#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworksservice.svc.cs#1)]
     [!code-vb[Data_WPFWCF#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworksservice.svc.vb#1)]  
  
     Esse código atualiza o `AdventureWorksService` classe, para que ela derive de uma <xref:System.Data.Services.DataService%601> que opera no `AdventureWorksLTEntities` classe de contexto no seu modelo de dados de entidade do objeto. Ele também atualiza o método `InitializeService` para permitir aos clientes do serviço acesso completo de leitura/gravação à entidade `SalesOrderHeader`.  
  
2.  Crie o projeto e verifique se ele foi criado sem erros.  
  
## <a name="create-the-wpf-client-application"></a>Criar o aplicativo cliente WPF  
 Para exibir os dados do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], crie um novo aplicativo WPF com uma fonte de dados que se baseie no serviço. A seguir neste passo a passo, você adicionará controles de associação de dados ao aplicativo.  
  
#### <a name="to-create-the-wpf-client-application"></a>Para criar o aplicativo cliente WPF  
  
1.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no nó da solução, clique em **Adicionar** e selecione **Novo Projeto**.  
  
2.  Na caixa de diálogo **Novo Projeto**, expanda **Visual Basic** ou **Visual C#** e selecione **Windows**.  
  
3.  Selecione o modelo de projeto **Aplicativo WPF**.  
  
4.  Na caixa **Nome**, digite `AdventureWorksSalesEditor` e clique em **OK**.  
  
     O Visual Studio adiciona o `AdventureWorksSalesEditor` projeto à solução.  
  
5.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
     A janela **Fontes de Dados** é aberta.  
  
6.  Na janela **Fontes de Dados**, clique em **Adicionar Nova Fonte de Dados**.  
  
     O **Assistente de Configuração de Fonte de Dados** é aberto.  
  
7.  Na página **Escolher um Tipo de Fonte de Dados** do assistente, selecione **Serviço** e clique em **Próximo**.  
  
8.  Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.  
  
     Visual Studio pesquisa a solução atual para os serviços disponíveis e adiciona `AdventureWorksService.svc` à lista de serviços disponíveis na **Services** caixa.  
  
9. No **Namespace** , digite `AdventureWorksService`.  
  
10. Na caixa **Serviços**, clique em **AdventureWorksService.svc** e em **OK**.  
  
     Visual Studio baixa a informações de serviço e, em seguida, retorna para o **configuração de fonte de dados** assistente.  
  
11. Na página **Adicionar Referência de Serviço**, clique em **Concluir**.  
  
     O Visual Studio adiciona nós que representam os dados retornados pelo serviço à janela **Fontes de Dados**.  
  
## <a name="define-the-user-interface-of-the-window"></a>Definir a interface do usuário da janela  
 Adicione vários botões à janela, modificando o XAML no WPF Designer. A seguir neste passo a passo, você adicionará código que permite aos usuários exibir e atualizar registros de vendas usando esses botões.  
  
#### <a name="to-create-the-window-layout"></a>Para criar o layout da janela  
  
1.  Na **Gerenciador de soluções**, clique duas vezes em MainWindow. XAML.  
  
     A janela é aberta no WPF Designer.  
  
2.  Na exibição [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] do designer, adicione o seguinte código entre as marcas `<Grid>`:  
  
    ```  
    <Grid.RowDefinitions>  
        <RowDefinition Height="75" />  
        <RowDefinition Height="525" />  
    </Grid.RowDefinitions>  
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>  
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>  
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>  
    ```  
  
3.  Compile o projeto.  
  
## <a name="create-the-data-bound-controls"></a>Criar os controles ligados a dados  
 Criar controles que exibem registros do cliente ao arrastar o `SalesOrderHeaders` nó a partir de **fontes de dados** janela no Designer.  
  
#### <a name="to-create-the-data-bound-controls"></a>Para criar os controles de associação de dados  
  
1. Na janela **Fontes de Dados**, clique no menu suspenso para o nó **SalesOrderHeaders** e selecione **Detalhes**.  
  
2. Expanda o nó **SalesOrderHeaders**.  
  
3. Neste exemplo, alguns campos não serão exibidos, portanto, clique no menu suspenso ao lado dos seguintes nós e selecione **Nenhum**:  
  
   - **CreditCardApprovalCode**  
  
   - **ModifiedDate**  
  
   - **OnlineOrderFlag**  
  
   - **RevisionNumber**  
  
   - **rowguid**  
  
     Essa ação impede que o Visual Studio crie controles de associação de dados para esses nós na etapa seguinte. Para este passo a passo, suponha que o usuário final não precisa ver esses dados.  
  
4. Na janela **Fontes de Dados**, arraste o nó **SalesOrderHeaders** para a linha de grade sob a linha que contém os botões.  
  
    O Visual Studio gera XAML e código que criam um conjunto de controles associados a dados na tabela **Produto**. Para obter mais informações sobre o XAML e o código gerado, consulte [WPF associar controles a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
5. No designer, clique na caixa de texto ao lado do rótulo de **ID do Cliente**.  
  
6. Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.  
  
7. Configure a propriedade **IsReadOnly** para cada uma das seguintes caixas de texto:  
  
   -   **Número da Ordem de Compra**  
  
   -   **ID da Ordem de Venda**  
  
   -   **Número da Ordem de Venda**  
  
## <a name="load-the-data-from-the-service"></a>Carregar os dados do serviço  
 Use o objeto de proxy de serviço para carregar dados de vendas do serviço. Em seguida, atribua os dados retornados para a fonte de dados para o <xref:System.Windows.Data.CollectionViewSource> na janela do WPF.  
  
#### <a name="to-load-the-data-from-the-service"></a>Para carregar os dados do serviço  
  
1.  No designer, para criar o `Window_Loaded` manipulador de eventos, clique duas vezes o texto que lê: **MainWindow**.  
  
2.  Substitua o manipulador de eventos pelo código a seguir. Substitua o endereço *localhost* neste código pelo endereço de host local no computador de desenvolvimento.  
  
     [!code-csharp[Data_WPFWCF#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFWCF#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#2)]  
  
## <a name="navigatesales-records"></a>Registros de Navigatesales  
 Adicione o código que permite aos usuários rolem nos registros de vendas, usando os botões **\<** e **>**.  
  
#### <a name="to-enable-users-to-navigate-sales-records"></a>Para permitir que os usuários naveguem nos registros de vendas  
  
1.  No designer, clique duas vezes no botão **<** na superfície da janela.  
  
     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `backButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Adicione o seguinte código ao manipulador de eventos `backButton_Click` gerado:  
  
     [!code-csharp[Data_WPFWCF#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFWCF#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#3)]  
  
3.  Retorne ao designer e clique duas vezes no botão **>**.  
  
     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `nextButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
4.  Adicione o seguinte código ao manipulador de eventos `nextButton_Click` gerado:  
  
     [!code-csharp[Data_WPFWCF#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFWCF#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#4)]  
  
## <a name="saving-changes-to-sales-records"></a>Salvando alterações em registros de vendas  
 Adicione o código que permite aos usuários exibir e salvar as alterações em registros de vendas usando o **salvar alterações** botão.  
  
#### <a name="to-add-the-ability-to-save-changes-to-sales-records"></a>Para adicionar a capacidade de salvar as alterações em registros de vendas  
  
1.  No designer, clique duas vezes no botão **Salvar Alterações**.  
  
     O Visual Studio abre o arquivo code-behind e cria um novo manipulador de eventos `saveButton_Click` para o evento <xref:System.Windows.Controls.Primitives.ButtonBase.Click>.  
  
2.  Adicione o seguinte código ao manipulador de eventos do `saveButton_Click`.  
  
     [!code-csharp[Data_WPFWCF#5](../snippets/csharp/VS_Snippets_ProTools/data_wpfwcf/cs/adventureworkssaleseditor/mainwindow.xaml.cs#5)]
     [!code-vb[Data_WPFWCF#5](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfwcf/vb/adventureworkssaleseditor/mainwindow.xaml.vb#5)]  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Compile e execute o aplicativo para verificar se é possível exibir e atualizar os registros do cliente.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Na **construir** menu, clique em **compilar solução**. Verifique se a solução é compilada sem erros.  
  
2.  Pressione **Ctrl + F5**.  
  
     O Visual Studio inicia o projeto **AdventureWorksService** sem depurá-lo.  
  
3.  No **Gerenciador de Soluções**, clique com o botão direito do mouse no projeto **AdventureWorksSalesEditor**.  
  
4.  No menu de contexto, em **Depurar**, clique em **Iniciar nova instância**.  
  
     O aplicativo é executado. Verifique o seguinte:  
  
    -   As caixas de texto exibem diferentes campos de dados desde o primeiro registro de venda, que tem a ID de ordem de venda **71774**.  
  
    -   Você pode clicar nos botões **>** ou **<** para navegar em outros registros de vendas.  
  
5.  Em um dos registros de vendas, digite algum texto na caixa **Comentário** e clique em **Salvar alterações**.  
  
6.  Feche o aplicativo e depois inicie-o novamente no Visual Studio.  
  
7.  Navegue até o registro de vendas que você alterou e verifique se a alteração persiste depois de fechar e reabrir o aplicativo.  
  
8.  Feche o aplicativo.  
  
## <a name="next-steps"></a>Próximas etapas  
 Depois de completar este passo a passo, você poderá realizar as seguintes tarefas relacionadas:  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para associar controles do WPF a outros tipos de fontes de dados. Para obter mais informações, consulte [controles de WPF associar a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md).  
  
-   Saiba como usar a janela **Fontes de Dados** no Visual Studio para exibir dados relacionados (isto é, dados em uma relação pai-filho) em controles do WPF. Para obter mais informações, confira [Passo a passo: Exibindo dados relacionados em um aplicativo WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md).  
  
## <a name="see-also"></a>Consulte também  
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Associar controles WPF a um conjunto de dados](../data-tools/bind-wpf-controls-to-a-dataset.md)   
 [Visão geral](http://msdn.microsoft.com/library/7924cf94-c9a6-4015-afc9-f5d22b1743bb)   
 [Visão geral do Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0)   
 [Visão de geral do Designer do Silverlight e WPF](http://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)   
 [Visão geral da vinculação de dados](http://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)
