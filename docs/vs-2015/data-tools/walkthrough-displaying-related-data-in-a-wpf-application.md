---
title: 'Walkthrough: Exibindo dados relacionados em um aplicativo do WPF | Microsoft Docs'
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
ms.assetid: 5c48f188-e9c4-40a6-97d9-67cdb2f90127
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 8116d4ab4a2f20f79f3849ae7f8b324af9832dd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850249"
---
# <a name="walkthrough-displaying-related-data-in-a-wpf-application"></a>Instruções passo a passo: exibindo dados relacionados em um aplicativo WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste tutorial, você criará um aplicativo WPF que exibe dados de tabelas de banco de dado que têm uma relação pai/filho. Os dados são encapsulados em entidades em uma Modelo de Dados de Entidade. A entidade pai contém informações de visão geral de um conjunto de pedidos. Cada propriedade dessa entidade está associada a um controle diferente no aplicativo. A entidade filho contém detalhes para cada pedido. Esse conjunto de dados está associado a um <xref:System.Windows.Controls.DataGrid> controle.

 Este passo a passo ilustra as seguintes tarefas:

- Criar um aplicativo do WPF e um Modelo de Dados de Entidade que é gerado a partir de dados no banco de dado de exemplo AdventureWorksLT.

- Criar um conjunto de controles vinculados a dados que exibem informações de visão geral de um conjunto de pedidos. Você cria os controles arrastando uma entidade pai da janela **fontes de dados** para **o designer do WPF**.

- Criando um <xref:System.Windows.Controls.DataGrid> controle que exibe detalhes relacionados para cada pedido selecionado. Você cria os controles arrastando uma entidade filho da janela **fontes de dados** para uma janela no **designer do WPF**.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos
 Você precisará dos seguintes componentes para concluir este passo a passo:

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

- Acesso a uma instância em execução do SQL Server ou SQL Server Express que tenha o banco de dados de exemplo AdventureWorksLT anexado a ele. Você pode baixar o banco de dados AdventureWorksLT do [site da CodePlex](https://codeplex.com/SqlServerSamples).

  Conhecimento prévio dos conceitos a seguir também é útil, mas não é necessário para concluir o passo a passo:

- Modelos de Dados de Entidade e o ADO.NET Entity Framework. Para obter mais informações, consulte [Entity Framework visão geral](https://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).

- Trabalhando com o WPF Designer. Para obter mais informações, consulte [visão geral do WPF e do designer do Silverlight](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62).

- Associação de dados do WPF. Para obter mais informações, consulte [visão geral da ligação de dados](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211).

## <a name="creating-the-project"></a>Criando o Projeto
 Crie um novo projeto do WPF para exibir os registros de pedidos.

#### <a name="to-create-a-new-wpf-project"></a>Para criar um novo projeto WPF

1. Inicie o Visual Studio.

2. No menu **Arquivo** , aponte para **Novo**e clique em **Projeto**.

3. Expanda **Visual C#** ou **Visual Basic**e, em seguida, selecione **Windows**.

4. Verifique se **.NET Framework 4** está selecionado na caixa de combinação na parte superior da caixa de diálogo. O <xref:System.Windows.Controls.DataGrid> controle que você usa neste passo a passos está disponível apenas no .NET Framework 4.

5. Selecione o modelo de projeto **Aplicativo WPF**.

6. Na caixa **Nome**, digite `AdventureWorksOrdersViewer`.

7. Clique em **OK**.

     O Visual Studio cria o `AdventureWorksOrdersViewer` projeto.

## <a name="creating-an-entity-data-model-for-the-application"></a>Criando um Modelo de Dados de Entidade para o aplicativo
 Antes de criar controles de associação de dados, você deve definir um modelo de dados para seu aplicativo e adicioná-lo à janela **Fontes de Dados**. Neste tutorial, o modelo de dados é um Modelo de Dados de Entidade.

#### <a name="to-create-an-entity-data-model"></a>Para criar um Modelo de Dados de Entidade

1. No menu **dados** , clique em **Adicionar nova fonte de dados** para abrir o **Assistente de configuração da fonte de dados**.

2. Na página **escolher um tipo de fonte de dados** , clique em **Database**e em **Avançar**.

3. Na página **escolher um modelo de banco de dados** , clique em **modelo de dados de entidade**e em **Avançar**.

4. Na página **escolher conteúdo do modelo** , clique em **gerar do banco de dados**e em **Avançar**.

5. Na página **escolher sua conexão de dados** , siga um destes procedimentos:

   - Se uma conexão de dados com o banco de dados de exemplo AdventureWorksLT estiver disponível na lista suspensa, selecione-a.

      - ou -

   - Clique em **nova conexão** e crie uma conexão com o banco de dados AdventureWorksLT.

     Verifique se a opção **salvar configurações de conexão de entidade no App.Config como** está selecionada e clique em **Avançar**.

6. Na página **escolher seus objetos de banco de dados** , expanda **tabelas**e selecione as seguintes tabelas:

   - **SalesOrderDetail**

   - **SalesOrderHeader**

7. Clique em **Concluir**.

8. Compile o projeto.

## <a name="creating-data-bound-controls-that-display-the-orders"></a>Criando controles vinculados a dados que exibem os pedidos
 Crie controles que exibam registros de pedidos arrastando a `SalesOrderHeaders` entidade da janela **fontes de dados** para o designer do WPF.

#### <a name="to-create-data-bound-controls-that-display-the-order-records"></a>Para criar controles vinculados a dados que exibem os registros de pedidos

1. Em **Gerenciador de soluções**, clique duas vezes em MainWindow. XAML.

    A janela é aberta no WPF Designer.

2. Edite o XAML para que as propriedades **Height** e **Width** sejam definidas como 800

3. Na janela **fontes de dados** , clique no menu suspenso do nó **SalesOrderHeaders** e selecione **detalhes**.

4. Expanda o nó **SalesOrderHeaders**.

5. Clique no menu suspenso ao lado de **SalesOrderID** e selecione **ComboBox**.

6. Para cada um dos nós filho a seguir do nó **SalesOrderHeaders** , clique no menu suspenso próximo ao nó e selecione **nenhum**:

   - **RevisionNumber**

   - **OnlineOrderFlag**

   - **ShipToAddressID**

   - **BillToAddressID**

   - **CreditCardApprovalCode**

   - **SubTotal**

   - **TaxAmt**

   - **Freight**

   - **ROWGUID**

   - **ModifiedDate**

     Essa ação impede que o Visual Studio crie controles de associação de dados para esses nós na etapa seguinte. Para este passo a passo, pressupõe-se que o usuário final não precise ver esses dados.

7. Na janela **fontes de dados** , arraste o nó **SalesOrderHeaders** para a janela no **designer do WPF**.

    O Visual Studio gera um XAML que cria um conjunto de controles associados a dados na entidade **SalesOrderHeaders** e o código que carrega os dados. Para obter mais informações sobre o XAML e o código gerados, consulte [associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

8. No designer, clique na caixa de combinação ao lado do rótulo **ID do pedido de vendas** .

9. Na janela **Propriedades**, marque a caixa de seleção ao lado da propriedade **IsReadOnly**.

## <a name="creating-a-datagrid-that-displays-the-order-details"></a>Criando um DataGrid que exibe os detalhes do pedido
 Crie um <xref:System.Windows.Controls.DataGrid> controle que exiba detalhes do pedido arrastando a `SalesOrderDetails` entidade da janela **fontes de dados** para o designer do WPF.

#### <a name="to-create-a-datagrid-that-displays-the-order-details"></a>Para criar um DataGrid que exibe os detalhes do pedido

1. Na janela **fontes de dados** , localize o nó **SalesOrderDetails** que é um filho do nó **SalesOrderHeaders** .

   > [!NOTE]
   > Também há um nó **SalesOrderDetails** que é um par do nó **SalesOrderHeaders** . Certifique-se de selecionar o nó filho do nó **SalesOrderHeaders** .

2. Expanda o nó de **SalesOrderDetails** filho.

3. Para cada um dos nós filho a seguir do nó **SalesOrderDetails** , clique no menu suspenso próximo ao nó e selecione **nenhum**:

   - **SalesOrderID**

   - **SalesOrderDetailID**

   - **ROWGUID**

   - **ModifiedDate**

     Essa ação impede que o Visual Studio inclua esses dados no <xref:System.Windows.Controls.DataGrid> controle que você cria na próxima etapa. Para este passo a passo, pressupõe-se que o usuário final não precise ver esses dados.

4. Na janela **Data Sources** , arraste o nó filho **SalesOrderDetails** para a janela no **designer do WPF**.

    O Visual Studio gera XAML para definir um novo controle vinculado a dados <xref:System.Windows.Controls.DataGrid> , e o controle aparece no designer. O Visual Studio também atualiza o `GetSalesOrderHeadersQuery` método gerado no arquivo code-behind para incluir os dados na entidade **SalesOrderDetails** .

## <a name="testing-the-application"></a>Testando o aplicativo
 Compile e execute o aplicativo para verificar se ele exibe os registros de pedidos.

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Pressione **F5**.

     O aplicativo é compilado e executado. Verifique o seguinte:

    - A caixa de combinação **ID do pedido de vendas** exibe **71774**. Esta é a primeira ID da ordem na entidade.

    - Para cada pedido selecionado na caixa de combinação **ID do pedido de vendas** , as informações detalhadas do pedido são exibidas no <xref:System.Windows.Controls.DataGrid> .

2. Feche o aplicativo.

## <a name="next-steps"></a>Próximas etapas
 Depois de concluir este passo a passos, saiba como usar a janela **fontes de dados** no Visual Studio para associar controles WPF a outros tipos de fontes de dados. Para obter mais informações, consulte [associar controles WPF a um WCF Data Service](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md) e [associar controles WPF a um conjunto](../data-tools/bind-wpf-controls-to-a-dataset.md)de dados.

## <a name="see-also"></a>Consulte Também
 [Associar controles WPF a dados no Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [exibir dados relacionados em aplicativos do WPF](../data-tools/display-related-data-in-wpf-applications.md)
