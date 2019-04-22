---
title: 'Passo a passo: Criando um serviço de dados do WCF com WPF e Entity Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 67b3034ee1d651289c167b894b0417d11b5995e8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59653080"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Passo a passo: Criando um WCF Data Service com o WPF e o Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este passo a passo demonstra como criar um simples [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] que é hospedado em um [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplicativo Web e, em seguida, acessá-lo de um aplicativo Windows Forms.  
  
 Neste passo a passo, você realizará as seguintes tarefas:  
  
-   Criará um aplicativo Web para hospedar um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Criará um [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] que representa a tabela Customers no banco de dados da Northwind.  
  
-   Criará um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Criará um aplicativo cliente e adicionará uma referência ao [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Habilitará a associação de dados ao serviço e gerará a interface de usuário.  
  
-   Se desejar, adicionará recursos de filtragem ao aplicativo.  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:  
  
-   O banco de dados de exemplo Northwind.  
  
     Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo partir o [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Para obter instruções, consulte [Downloading Sample Databases](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Criando o serviço  
 Para criar um [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], você adicionará um projeto Web, criará um [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] e, em seguida, criará o serviço usando o modelo.  
  
 Na primeira etapa, você adicionará um projeto Web para hospedar o serviço.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Para criar o projeto Web  
  
1. Na barra de menus, escolha **arquivo**, **New**, **projeto**.  
  
2. Na caixa de diálogo **Novo Projeto**, expanda os nós **Visual Basic** ou **Visual C#** e **Web** e escolha o modelo **Aplicativo Web ASP .NET**.  
  
3. Na caixa de texto **Nome**, insira **NorthwindWeb** e escolha o botão **OK**.  
  
4. Na caixa de diálogo **Novo Projeto ASP.NET**, na lista **Selecionar um modelo**, escolha **Vazio** e o botão **OK**.  
  
   Nesta etapa, você criará um [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] que representa a tabela Customers no banco de dados da Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Para criar o Modelo de Dados de Entidade  
  
1. Na barra de menus, escolha **Project**, **Adicionar Novo Item**.  
  
2. Na caixa de diálogo **Adicionar Novo Item**, escolha o nó **Dados** e, em seguida, o item **Modelo de Dados de Entidade ADO.NET**.  
  
3. No **nome** texto, digite `NorthwindModel`e, em seguida, escolha o **Add** botão.  
  
    O Assistente do Modelo de Dados de Entidade é aberto.  
  
4. No Assistente de modelo de dados de entidade, na **escolher conteúdo do modelo** , escolha o **EF Designer do banco de dados** item e, em seguida, escolha o **próxima** botão.  
  
5. Na página **Escolha a Conexão de Dados**, executa uma das seguintes etapas:  
  
   -   Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-a.  
  
        - ou -  
  
   -   Escolha o botão **Nova Conexão** para configurar uma nova conexão de dados. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).  
  
6. Se o banco de dados exigir uma senha, escolha o botão de opção **Sim, incluir os dados confidenciais da cadeia de conexão** e escolha o botão **Avançar**.  
  
   > [!NOTE]
   >  Se uma caixa de diálogo for exibida, escolha **Sim** para salvar o arquivo no seu projeto.  
  
7. Na página **Escolha sua versão**, escolha o botão de opção **Entity Framework 5.0** e o botão **Avançar**.  
  
   > [!NOTE]
   >  Para usar a versão mais recente do Entity Framework 6 com Serviço WCF, você precisará instalar o pacote NuGet do provedor do Entity Framework do WCF Data Services. Ver [usar o WCF Data Services 5.6.0 com o Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. Na página **Escolher Objetos do Banco de Dados**, expanda o nó **Tabelas**, marque a caixa de seleção **Clientes** e escolha o botão **Concluir**.  
  
    O diagrama do modelo da entidade será exibido e um arquivo NorthwindModel.edmx será adicionado ao projeto.  
  
   Nesta etapa, você vai criar e testar o serviço de dados.  
  
#### <a name="to-create-the-data-service"></a>Para criar o serviço de dados  
  
1. Na barra de menus, escolha **Project**, **Adicionar Novo Item**.  
  
2. Na caixa de diálogo **Adicionar Novo Item**, escolha o nó **Web** e, em seguida, o item **WCF Data Services 5.6**.  
  
3. No **nome** texto, digite `NorthwindCustomers`e, em seguida, escolha o **Add** botão.  
  
    O arquivo Northwindcustomers SVC aparece na **Editor de códigos**.  
  
4. No **Editor de Códigos**, localize o primeiro comentário `TODO:` e substitua o código pelo seguinte:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Substitua os comentários no manipulador de eventos `InitializeService` pelo seguinte código:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. Na barra de menus, escolha **Debug**, **Start Without Debugging** para executar o serviço. Uma janela do navegador é aberta e o esquema XML do serviço é exibido.  
  
7. No **endereço** barra, insira `Customers` no final da URL para Northwindcustomers e, em seguida, escolha o **ENTER** chave.  
  
    É exibida uma representação XML dos dados na tabela Customers.  
  
   > [!NOTE]
   >  Em alguns casos, o Internet Explorer interpretará incorretamente os dados como um RSS feed. Você deve verificar se a opção para exibir RSS feeds está desabilitada. Para obter mais informações, consulte [solução de problemas de referências de serviço](../data-tools/troubleshooting-service-references.md).  
  
8. Feche a janela do navegador.  
  
   Nas próximas etapas, você criará um aplicativo cliente do Windows Forms para consumir o serviço.  
  
## <a name="creating-the-client-application"></a>Criando o aplicativo cliente  
 Para criar o aplicativo cliente, você vai adicionar um segundo projeto, adicionar uma referência de serviço ao projeto, configurar uma fonte de dados e criar uma interface do usuário para exibir os dados do serviço.  
  
 Na primeira etapa, você vai adicionar um projeto do Windows Forms à solução e defini-lo como o projeto de inicialização.  
  
#### <a name="to-create-the-client-application"></a>Para criar o aplicativo cliente  
  
1. Na barra de menus, escolha arquivo, **Add**, **novo projeto**.  
  
2. No **novo projeto** diálogo caixa, expanda o **Visual Basic** ou **Visual c#** nó e escolha o **Windows** nó e, em seguida, escolha  **Aplicativo de formulários do Windows**.  
  
3. Na caixa de texto **Nome**, insira `NorthwindClient` e, em seguida, escolha o botão **OK**.  
  
4. No **Gerenciador de Soluções**, escolha o nó de projeto **NorthwindClient**.  
  
5. Na barra de menus, escolha **Projeto**, **Definir como Projeto de Inicialização**.  
  
   Nesta etapa, você adicionará uma referência de serviço ao [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] no projeto Web.  
  
#### <a name="to-add-a-service-reference"></a>Para adicionar uma referência de serviço  
  
1. Na barra de menus, escolha **Project**, **Add Service Reference**.  
  
2. Na caixa de diálogo **Adicionar Referência de Serviço**, escolha o botão **Descobrir**.  
  
    A URL do serviço NorthwindCustomers é exibida no campo **Endereço**.  
  
3. Escolha o botão **OK** para adicionar a referência de serviço.  
  
   Nesta etapa, você vai configurar um fonte de dados para habilitar a associação de dados ao serviço.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Para habilitar a associação de dados ao serviço  
  
1. Na barra de menus, escolha **modo de exibição**, **Other Windows**, **fontes de dados**.  
  
2. Na janela **Fontes de Dados**, escolha o botão **Adicionar Nova Fonte de Dados**.  
  
3. Na página **Escolher um Tipo de Fonte de Dados** do **Assistente de Configuração de Fonte de Dados**, escolha **Objeto** e, em seguida, o botão **Próximo**.  
  
4. Na página **Selecionar os Objetos de Dados**, expanda os nós **NorthwindClient** e **NorthwindClient.ServiceReference1**.  
  
5. Marque a caixa de seleção **Customer** e escolha o botão **Finalizar**.  
  
   Nesta etapa, você criará a interface do usuário que exibirá os dados do serviço.  
  
#### <a name="to-create-the-user-interface"></a>Para criar a interface do usuário  
  
1. Na janela **Fontes de Dados**, abra o menu de atalho do nó **Clientes** e escolha **Copiar**.  
  
2. No designer de formulários **Form1.vb** ou **Form1.cs**, abra o menu de atalho e escolha **Colar**.  
  
    Um controle <xref:System.Windows.Forms.DataGridView>, um componente <xref:System.Windows.Forms.BindingSource> e um componente <xref:System.Windows.Forms.BindingNavigator> são adicionados ao formulário.  
  
3. Escolha o **CustomersDataGridView** controle e, em seguida, no **propriedades** conjunto de janela a **Dock** propriedade a ser **preencher**.  
  
4. Na **Gerenciador de soluções**, abra o menu de atalho para o **Form1** nó e escolha **Exibir código** para abrir o Editor de códigos e adicione as seguintes importações ou usando a instrução no parte superior do arquivo:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Adicione o seguinte código ao manipulador de eventos do `Form1_Load`:  
  
   ```vb  
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
           Dim proxy As New NorthwindEntities _  
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
           Me.CustomersBindingSource.DataSource = proxy.Customers  
       End Sub  
   ```  
  
   ```csharp  
   private void Form1_Load(object sender, EventArgs e)  
   {  
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
   this.CustomersBindingSource.DataSource = proxy.Customers;  
   }  
  
   ```  
  
6. Na **Gerenciador de soluções**, abra o menu de atalho para o arquivo Northwindcustomers SVC e escolha **exibir no navegador**. O Internet Explorer é aberto e o esquema XML do serviço é exibido.  
  
7. Copie a URL da barra de endereços do Internet Explorer.  
  
8. No código que você adicionou na etapa 4, selecione `http://localhost:53161/NorthwindCustomers.svc/` e o substitua pela URL que acabou de copiar.  
  
9. Na barra de menus, escolha **Debug**, **iniciar depuração** para executar o aplicativo. As informações do cliente são exibidas.  
  
   Agora você tem um aplicativo funcional que exibe uma lista de clientes do serviço NorthwindCustomers. Se desejar expor dados adicionais por meio do serviço, você pode modificar o [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] para incluir tabelas adicionais do banco de dados da Northwind.  
  
   Na próxima etapa opcional, você aprenderá como filtrar os dados que são retornados pelo serviço.  
  
## <a name="adding-filtering-capabilities"></a>Adicionando recursos de filtragem  
 Nesta etapa, você personalizará o aplicativo para filtrar os dados por cidade do cliente.  
  
#### <a name="to-add-filtering-by-city"></a>Para adicionar a filtragem por cidade  
  
1.  No **Gerenciador de Soluções**, abra o menu de atalho do nó **Form1.vb** ou **Form1.cs** e escolha **Abrir**.  
  
2.  Adicione um controle <xref:System.Windows.Forms.TextBox> e um controle <xref:System.Windows.Forms.Button> da **Caixa de Ferramentas** ao formulário.  
  
3.  Abra o menu de atalho para o <xref:System.Windows.Forms.Button> controlar e, em seguida, escolha **Exibir código**e, em seguida, adicione o seguinte código no `Button1_Click` manipulador de eventos:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  No código anterior, substitua `http://localhost:53161/NorthwindCustomers.svc` pela URL do manipulador de eventos `Form1_Load`.  
  
5.  Na barra de menus, escolha **Debug**, **iniciar depuração** para executar o aplicativo.  
  
6.  Na caixa de texto, insira **Londres** e escolha o botão. Somente os clientes de London são exibidos.  
  
## <a name="see-also"></a>Consulte também  
 [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Como: Adicionar, atualizar ou remover uma referência do WCF Data Service](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
