---
title: 'Passo a passo: Criando um aplicativo de dados de N camadas | Microsoft Docs'
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
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3185a6b7ebe4f5f37428e04f1b4215431921c51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924463"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Passo a passo: Criando um aplicativo de dados de N camadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-camadas * aplicativos de dados são aplicativos que acessam dados e são separados em várias camadas de lógicas, ou *camadas*. A separação de componentes de aplicativos em camadas discretas aumenta a capacidade de manutenção e a escalabilidade do aplicativo. Isso é feito pela adoção com mais facilidade de novas tecnologias que podem ser aplicadas a uma única camada, sem precisar reprojetar toda a solução. A arquitetura de N camadas inclui uma camada de apresentação, uma camada intermediária e uma camada de dados. A camada intermediária geralmente inclui uma camada de acesso a dados, uma camada lógica de negócios e componentes compartilhados, tais como autenticação e validação. A camada de dados inclui um banco de dados relacional. Os aplicativos de N camadas geralmente armazenam informações confidenciais na camada de acesso a dados da camada intermediária para manter o isolamento de usuários finais que acessam a camada de apresentação. Para obter mais informações, consulte [visão geral dos aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).  
  
 Uma maneira de separar as várias camadas em um aplicativo de N camadas é criar projetos discretos para cada camada que você deseja incluir em seu aplicativo. Os conjuntos de dados digitados contêm uma propriedade `DataSet Project` que determina quais projetos o conjunto de dados gerado e o código `TableAdapter` devem acessar.  
  
 Esse passo a passo demonstra como separar o conjunto de dados e o código `TableAdapter` em projetos de biblioteca de classes discretas usando o **Designer de Conjunto de Dados**. Após você separar o conjunto de dados e o código TableAdapter, você criará um [serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) serviço para chamar a camada de acesso a dados. Finalmente, você criará um aplicativo do Windows Forms como a camada de apresentação. Essa camada acessa dados do serviço de dados.  
  
 Durante este passo a passo, você executará as seguintes etapas:  
  
- Criar uma nova solução de N camadas que conterá vários projetos.  
  
- Adicionar dois projetos de bibliotecas de classes na solução de N camadas.  
  
- Criar um conjunto de dados tipado usando o **Assistente de Configuração de Fonte de Dados**.  
  
- Separar gerado [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e o código do conjunto de dados em projetos discretos.  
  
- Criar um serviço do Windows Communication Foundation (WCF) a ser chamado na camada de acesso a dados.  
  
- Criar funções no serviço para recuperar dados da camada de acesso a dados.  
  
- Criar um aplicativo do Windows Forms para servir como a camada de apresentação.  
  
- Criar controles do Windows Forms associados à fonte de dados.  
  
- Gravar código para preencher as tabelas de dados.  
  
  ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") para uma versão em vídeo deste tópico, consulte [vídeo de instruções: Criando um aplicativo de dados de N camadas](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Pré-requisitos  
 Para concluir esta explicação passo a passo, será necessário:  
  
-   Acesso ao banco de dados de exemplo Northwind.
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Criando a solução de N camadas e a biblioteca de classes para manter o conjunto de dados (DataEntityTier)  
 A primeira etapa deste passo a passo é criar uma solução e dois projetos de biblioteca de classes. A primeira biblioteca de classes manterá o conjunto de dados (a classe DataSet digitada gerada e DataTables, que manterá os dados do aplicativo). Este projeto é usado como a camada de entidade de dados do aplicativo e geralmente está localizada na camada intermediária. O Designer de conjunto de dados é usado para criar o conjunto de dados inicial e separar automaticamente o código em duas bibliotecas de classes.  
  
> [!NOTE]
>  Dê o nome correto ao projeto e à solução antes de clicar em **OK**. Isso facilitará a conclusão deste passo a passo.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Para criar a solução de N camadas e a biblioteca de classes DataEntityTier  
  
1.  Dos **arquivo** menu, crie um novo projeto.  
  
    > [!NOTE]
    >  O **Dataset Designer** tem suporte no [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e projetos c#. Crie o novo projeto em uma dessas linguagens.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, clique em **Windows**.  
  
3.  Clique o **biblioteca de classes** modelo.  
  
4.  Nomeie o projeto como **DataEntityTier**.  
  
5.  Nomeie a solução **NTierWalkthrough**.  
  
6.  Clique em **OK**.  
  
     Uma solução NTierWalkthrough que contém o projeto DataEntityTier é criada e adicionada ao **Gerenciador de Soluções**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Criando a biblioteca de classes para manter os TableAdapters (DataAccessTier)  
 A próxima etapa após a criação do projeto DataEntityTier é criar outro projeto de biblioteca de classes. Esse projeto conterá o gerado `TableAdapter`s e é chamado de *camada de acesso de dados* do aplicativo. A camada de acesso a dados contém as informações necessárias para se conectar ao banco de dados e geralmente está localizada na camada intermediária.  
  
#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Para criar a nova biblioteca de classes para os TableAdapters  
  
1.  Dos **arquivo** menu, adicione um novo projeto à solução NTierWalkthrough.  
  
2.  No **novo projeto** na caixa de **modelos** painel, clique em **biblioteca de classes**.  
  
3.  Nomeie o projeto **DataAccessTier** e clique em **Okey**.  
  
     O projeto DataAccessTier é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Criando o conjunto de dados  
 A próxima etapa é criar um conjunto de dados tipado. Os conjuntos de dados tipado são criados com a classe do conjunto de dados (incluindo as classes DataTables) e as classes `TableAdapter` em um único projeto. (Todas as classes são geradas em um único arquivo.) Quando você separa o conjunto de dados e os `TableAdapter`s em projetos diferentes, é a classe do conjunto de dados que é movida para o outro projeto, mantendo as classes `TableAdapter` no projeto original. Portanto, crie o conjunto de dados no projeto que conterá, por fim, os `TableAdapter`s (o projeto DataAccessTier). Você criará o conjunto de dados usando o **Data Source Configuration Wizard**.  
  
> [!NOTE]
> É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.
  
#### <a name="to-create-the-dataset"></a>Para criar o conjunto de dados  
  
1.  Clique em DataAccessTier em **Gerenciador de soluções**.  
  
2.  No menu **Dados**, clique em **Mostrar Fontes de Dados**.  
  
3.  No **fontes de dados** janela, clique em **Add New Data Source** para iniciar o **Data Source Configuration Wizard**.  
  
4.  Sobre o **escolher um tipo de fonte de dados** , clique em **banco de dados** e, em seguida, clique em **próxima**.  
  
5.  Na página **Escolha a Conexão de Dados**, execute uma das seguintes ações:  
  
     Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.  
  
     - ou -  
  
     Clique em **nova Conexão** para abrir o **Adicionar Conexão** caixa de diálogo.  
  
6.  Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.  
  
    > [!NOTE]
    >  Se você escolheu um arquivo do banco de dados local (em vez de se conectar ao SQL Server), talvez seja perguntado se deseja adicionar o arquivo ao projeto. Clique em **Sim** para adicionar o arquivo de banco de dados ao projeto.  
  
7.  Clique em **próxima** sobre o **salvar a cadeia de Conexão no arquivo de configuração de aplicativo** página.  
  
8.  Expanda o nó **Tabelas** na página **Escolher Objetos do Banco de Dados**.  
  
9. Marque as caixas de seleção para o **clientes** e **pedidos** tabelas e clique **concluir**.  
  
     NorthwindDataSet é adicionado ao projeto DataAccessTier e aparece na janela **Fontes de Dados**.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Separando os TableAdapters do Conjunto de Dados  
 Depois de criar o conjunto de dados, separe a classe do conjunto de dados gerada a partir dos TableAdapters. Você faz isso ao configurar a propriedade **Projeto do Conjunto de Dados** para o nome do projeto que armazenará a classe do conjunto de dados separada.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Para separar os TableAdapters do Conjunto de Dados  
  
1. Clique duas vezes em **NorthwindDataSet.xsd** no **Gerenciador de Soluções** para abrir o conjunto de dados no **Designer de Conjunto de Dados**.  
  
2. Clique em uma área vazia no designer.  
  
3. Localize o nó **Projeto do Conjunto de Dados** na janela **Propriedades**.  
  
4. No **projeto DataSet** , clique em **DataEntityTier**.  
  
5. No menu **Compilar**, clique em **Compilar Solução**.  
  
   O conjunto de dados e os TableAdapters são separados em dois projetos de biblioteca de classes. O projeto que continha originalmente todo o conjunto de dados (DataAccessTier) contém agora somente os TableAdapters. O projeto atribuído a **projeto DataSet** propriedade (DataEntityTier) contém o conjunto de dados tipado: NorthwindDataSet (ou NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Quando você separa os conjuntos de dados e os TableAdapters (configurando a propriedade **Projeto de Conjunto de Dados**), as classes dos conjuntos de dados parciais existentes no projeto não são movidas automaticamente. As classes parciais do conjunto de dados existentes devem ser movidas manualmente para o projeto do conjunto de dados.  
  
## <a name="creating-a-new-service-application"></a>Criando um novo aplicativo de serviço  
 Como este passo a passo demonstra como acessar a camada de acesso a dados usando um serviço WCF, crie um novo aplicativo de serviço WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Para criar um novo aplicativo de Serviço WCF  
  
1.  Dos **arquivo** menu, adicione um novo projeto à solução NTierWalkthrough.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, clique em **WCF**. No **modelos** painel, clique em **WCF Service Library**.  
  
3.  Nomeie o projeto **DataService** e clique em **Okey**.  
  
     O projeto DataService é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Criando métodos na camada de acesso a dados para retornar os dados de clientes e pedidos  
 O serviço de dados tem que chamar dois métodos na camada de acesso a dados: GetCustomers e GetOrders. Esses métodos retornarão as tabelas Clientes e Pedidos do Northwind. Crie os métodos GetCustomers e GetOrders no projeto DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Para criar um método na camada de acesso a dados que retorna a tabela Clientes  
  
1.  Na **Gerenciador de soluções**, clique duas vezes em NorthwindDataSet para abrir o conjunto de dados no Designer de conjunto de dados.  
  
2.  Clique com botão direito CustomersTableAdapter e clique em **Add Query** para editar o Tableadapter.  
  
3.  Na página **Escolher um Tipo de Comando**, mantenha o valor padrão de **Usar instruções SQL** e clique em **Próximo**.  
  
4.  Na página **Escolher um Tipo de Consulta**, mantenha o valor padrão de **SELECT que retorna linhas** e clique em **Próximo**.  
  
5.  Na página **Especificar uma instrução SQL SELECT**, mantenha a consulta padrão e clique em **Próximo**.  
  
6.  Na página **Escolher Métodos a Serem Gerados**, digite **GetCustomers** para o **Nome do método** na seção **Retornar uma DataTable**.  
  
7.  Clique em **Finalizar**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Para criar um método na camada de acesso a dados que retorna a tabela Pedidos  
  
1.  Clique com botão direito OrdersTableAdapter e clique em **Add Query**.  
  
2.  Na página **Escolher um Tipo de Comando**, mantenha o valor padrão de **Usar instruções SQL** e clique em **Próximo**.  
  
3.  Na página **Escolher um Tipo de Consulta**, mantenha o valor padrão de **SELECT que retorna linhas** e clique em **Próximo**.  
  
4.  Na página **Especificar uma instrução SQL SELECT**, mantenha a consulta padrão e clique em **Próximo**.  
  
5.  Na página **Escolher Métodos a Serem Gerados**, digite **GetOrders** para o **Nome do método** na seção **Retornar uma DataTable**.  
  
6.  Clique em **Finalizar**.  
  
7.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Adicionando uma referência à entidade de dados e às camadas de acesso a dados para o serviço de dados  
 Como o serviço de dados requer informações do conjunto de dados e dos TableAdapters, adicione referências aos projetos DataEntityTier e DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Para adicionar referência aos serviço de dados  
  
1.  Clique com botão direito DataService na **Gerenciador de soluções** e clique em **adicionar referência**.  
  
2.  Clique na guia **Projetos** na caixa de diálogo **Adicionar Referência**.  
  
3.  Escolha os projetos **DataAccessTier** e **DataEntityTier**.  
  
4.  Clique em **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Adicionando funções ao serviço para chamar os métodos GetCustomers e GetOrders na camada de acesso a dados  
 Agora que a camada de acesso a dados contém os métodos para retornar dados, crie métodos no serviço de dados para chamar os métodos na camada de acesso a dados.  
  
> [!NOTE]
>  Para projetos C#, adicione uma referência ao assembly `System.Data.DataSetExtensions` para que o código a seguir seja compilado.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Para criar as funções GetCustomers e GetOrders no serviço de dados  
  
1.  No **DataService** do projeto, clique duas vezes em IService1.vb ou IService1.cs.  
  
2.  Adicione o seguinte código no comentário **Adicionar suas operações de serviço aqui**:  
  
    ```vb  
    <OperationContract()> _  
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable  
  
    <OperationContract()> _  
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable  
    ```  
  
    ```csharp  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();  
  
    [OperationContract]  
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();  
  
    ```  
  
3.  No projeto DataService, dê um clique duplo em Service1.vb (ou Service1.cs).  
  
4.  Adicione o seguinte código à classe Service1:  
  
    ```vb  
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers  
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
        Return CustomersTableAdapter1.GetCustomers()  
    End Function  
  
    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders  
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
        Return OrdersTableAdapter1.GetOrders()  
    End Function  
    ```  
  
    ```csharp  
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter  
             CustomersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();  
        return CustomersTableAdapter1.GetCustomers();  
  
    }  
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()  
    {  
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter  
             OrdersTableAdapter1  
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();  
        return OrdersTableAdapter1.GetOrders();  
  
    }  
    ```  
  
5.  No menu **Compilar**, clique em **Compilar Solução**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Criando uma camada de apresentação para exibir dados a partir do serviço de dados  
 Agora que a solução contém o serviço de dados que possui métodos chamados na camada de acesso a dados, crie outro projeto que será chamado no serviço de dados e apresente os dados aos usuários. Neste passo a passo, crie um aplicativo do Windows Forms, o qual será a camada de apresentação do aplicativo de N camadas.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Para criar o projeto da camada de apresentação  
  
1.  Dos **arquivo** menu, adicione um novo projeto à solução NTierWalkthrough.  
  
2.  No **novo projeto** na caixa de **tipos de projeto** painel, clique em **Windows**. No **modelos** painel, clique em **aplicativo de formulários do Windows**.  
  
3.  Nomeie o projeto como **PresentationTier** e clique em **OK**.  
  
4.  O projeto PresentationTier é criado e adicionado à solução NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Configurando o projeto PresentationTier como o projeto de inicialização  
 Como a camada de apresentação é o aplicativo cliente real usado para apresentar e interagir com os dados, você deve configurar o projeto PresentationTier para ser o projeto de inicialização.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Para configurar o novo projeto de camada de apresentação como o projeto de inicialização  
  
-   Em **Gerenciador de Soluções**, clique com o botão direito do mouse em **PresentationTier** e clique em **Definir como Projeto de Inicialização**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Adicionando referências à camada de apresentação  
 O aplicativo cliente PresentationTier requer uma referência de serviço para o serviço de dados a fim de acessar os métodos no serviço. Além disso, uma referência ao conjunto de dados é necessária para permitir o compartilhamento de tipos pelo serviço WCF. O código adicionado à classe do conjunto de dados parcial estará disponível na camada de apresentação somente após você permitir o compartilhamento de tipos por meio do serviço de dados. Como você geralmente adiciona código como validação para os eventos de alteração de linha e coluna de uma tabela de dados, é provável que você queira acessar esse código a partir do cliente.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Para adicionar uma referência à camada de apresentação  
  
1.  Na **Gerenciador de soluções**, clique com botão direito PresentationTier e clique em **adicionar referência**.  
  
2.  No **adicionar referência** caixa de diálogo, clique o **projetos** guia.  
  
3.  Selecione **DataEntityTier** e clique em **Okey**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Para adicionar uma referência de serviço à camada de apresentação  
  
1.  Na **Gerenciador de soluções**, clique com botão direito PresentationTier e clique em **Add Service Reference**.  
  
2.  Na caixa de diálogo **Adicionar Referência de Serviço**, clique em **Descobrir**.  
  
3.  Selecione **Service1** e clique em **Okey**.  
  
    > [!NOTE]
    >  Se você tiver vários serviços no computador atual, escolha o serviço criado anteriormente neste passo a passo (o serviço que contém os métodos GetCustomers e GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Adicionando DataGridViews ao formulário para exibir os dados retornados pelo serviço de dados  
 Depois de adicionar a referência de serviço ao serviço de dados, a janela **Fontes de Dados** é preenchida automaticamente com os dados retornados pelo serviço.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Para adicionar duas associações de dados DataGridViews ao formulário  
  
1.  Na **Gerenciador de soluções**, selecione o projeto PresentationTier.  
  
2.  Na janela **Fontes de Dados**, expanda **NorthwindDataSet** e localize o nó **Clientes**.  
  
3.  Arraste o nó **Clientes** para Form1.  
  
4.  Na janela **Fontes de Dados**, expanda o nó **Clientes** e localize o nó **Pedidos** relacionado (o nó **Pedidos** aninhado no nó **Clientes**).  
  
5.  Arraste o nó **Pedidos** relacionado para Form1.  
  
6.  Crie um manipulador de eventos `Form1_Load` ao clicar duas vezes em uma área vazia do formulário.  
  
7.  Adicione o seguinte código ao manipulador de eventos do `Form1_Load`.  
  
    ```vb  
    Dim DataSvc As New ServiceReference1.Service1Client  
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)  
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)  
    ```  
  
    ```csharp  
    ServiceReference1.Service1Client DataSvc =   
        new ServiceReference1.Service1Client();  
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());  
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());  
  
    ```  
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Aumentando o tamanho máximo da mensagem permitida pelo serviço  
 Como o serviço retorna dados das tabelas Clientes e Pedidos, o valor padrão para maxReceivedMessageSize não é grande o suficiente para manter os dados e deve ser ampliado. Neste passo a passo, você alterará o valor para 6553600. Você alterará o valor no cliente e isso atualizará automaticamente a referência de serviço.  
  
> [!NOTE]
>  O menor tamanho padrão se destina a limitar a exposição para ataques de negação de serviço (DoS). Para obter mais informações, consulte <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Para aumentar o valor maxReceivedMessageSize  
  
1.  Na **Gerenciador de soluções**, duas vezes no arquivo App. config no projeto PresentationTier.  
  
2.  Encontre o atributo de tamanho **maxReceivedMessage** e altere o valor para `6553600`.  
  
## <a name="testing-the-application"></a>Testando o aplicativo  
 Execute o aplicativo. Os dados são recuperados a partir do serviço de dados e exibidos no formulário.  
  
#### <a name="to-test-the-application"></a>Para testar o aplicativo  
  
1.  Pressione F5.  
  
2.  Os dados das tabelas Clientes e Pedidos são recuperados a partir do serviço de dados e exibidos no formulário.  
  
## <a name="next-steps"></a>Próximas etapas  
 Dependendo dos requisitos do aplicativo, existem várias etapas que você talvez queira realizar após salvar os dados relacionados no aplicativo baseado em Windows. Por exemplo, você poderia fazer as seguintes melhorias a este aplicativo:  
  
-   Adicionar validação ao conjunto de dados. Para obter informações, consulte [passo a passo: Adicionando validação a um aplicativo de dados de N camadas](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).  
  
-   Adicionar métodos adicionais ao serviço para atualizar dados novamente no banco de dados.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Atualização hierárquica](../data-tools/hierarchical-update.md)   
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
