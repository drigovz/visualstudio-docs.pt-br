---
title: Passar dados entre formulários | Microsoft Docs
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
- walkthroughs [Windows Forms], data
- walkthroughs [Visual Studio], data
- data [Visual Studio], passing between forms
- forms, passing data between
- Windows Forms, walkthroughs
ms.assetid: 78bf038b-9296-4fbf-b0e8-d881d1aff0df
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e14165ba2111f40898c00b3d01950425c042070
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652907"
---
# <a name="pass-data-between-forms"></a>Passar dados entre formulários
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este passo a passo fornece instruções detalhadas de como passar os dados de um formulário para outro. Usando as tabelas Customers e Orders da Northwind, um formulário permite que os usuários selecionem um cliente e um segundo formulário exibe os pedidos do cliente selecionado. Este tutorial mostra como criar um método no segundo formulário que recebe dados do primeiro formulário.

> [!NOTE]
> Este passo a passo demonstra apenas uma maneira de passar dados entre formulários. Há outras opções para passar dados para um formulário, incluindo a criação de um segundo construtor para receber dados ou a criação de uma propriedade pública que pode ser definida com dados do primeiro formulário.

 As tarefas ilustradas neste passo a passo incluem:

- Criando um novo projeto de **aplicativo do Windows** .

- Criando e configurando um conjunto de dados com o [Assistente de configuração de fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Selecionando o controle a ser criado no formulário ao arrastar itens da janela **Fontes de Dados**. Para obter mais informações, consulte [definir o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Criar controles associados a dados arrastando itens da janela **Fontes de Dados** para um formulário.

- Criar um segundo formulário com uma grade para exibir dados.

- Criar uma consulta TableAdapter para buscar pedidos de um cliente específico.

- Passar dados entre formulários.

## <a name="prerequisites"></a>Prerequisites
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-the-windows-application"></a>Criar o aplicativo do Windows

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No menu **arquivo** , crie um novo projeto.

2. Nomeie o projeto `PassingDataBetweenForms`.

3. Selecione **Windows Forms aplicativo**e clique em **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **PassingDataBetweenForms** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="create-the-data-source"></a>Criar a fonte de dados

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

2. Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o assistente de **Configuração de Fonte de Dados**.

3. Selecione **Banco de Dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, clique em **Avançar**.

4. Na página **Escolha um Modelo de Banco de Dados**, verifique se o **Conjunto de dados** foi especificado e clique em **Avançar**.

5. Na página **Escolha a Conexão de Dados**, faça o seguinte:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **Nova Conexão** para inicializar a caixa de diálogo **Adicionar/Modificar Conexão**.

6. Se o banco de dados exigir uma senha e a opção para incluir dados confidenciais estiver habilitada, clique em **Avançar**.

7. Na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** , clique em **Avançar**.

8. Na página **escolher seus objetos de banco de dados** , expanda o nó **tabelas** .

9. Selecione as tabelas **Customers** e **Orders** e, em seguida, clique em **Finalizar**.

     O **NorthwindDataSet** é adicionado ao projeto e as tabelas **Customers** e **Orders** aparecem na janela **Fontes de Dados**.

## <a name="create-the-first-form-form1"></a>Criar o primeiro formulário (Form1)
 Você pode criar uma grade de associação de dados (um controle <xref:System.Windows.Forms.DataGridView>), arrastando o nó **Clientes** da janela **Fontes de Dados** para o formulário.

#### <a name="to-create-a-data-bound-grid-on-the-form"></a>Para criar uma grade de associação de dados no formulário

- Arraste o nó principal **Clientes** da janela **Fontes de Dados** para **Form1**.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no **Form1**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

## <a name="create-the-second-form-form2"></a>Criar o segundo formulário (Form2)

#### <a name="to-create-a-second-form-to-pass-the-data-to"></a>Para criar um segundo formulário para o qual passar os dados

1. No menu **Projeto**, escolha **Adicionar Formulário do Windows**.

2. Deixe o nome padrão **Form2** e clique em **Adicionar**.

3. Arraste o nó principal **Pedidos** da janela **Fontes de Dados** para **Form2**.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no **Form2**. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

4. Exclua o **OrdersBindingNavigator** da bandeja de componentes.

     O **OrdersBindingNavigator** desaparece do **Form2**.

## <a name="add-a-tableadapter-query-to-form2-to-load-orders-for-the-selected-customer-on-form1"></a>Adicionar uma consulta do TableAdapter ao Form2 para carregar pedidos para o cliente selecionado no Form1

#### <a name="to-create-a-tableadapter-query"></a>Para criar uma consulta do TableAdapter

1. Clique duas vezes no arquivo **NorthwindDataSet.xsd** no **Gerenciador de Soluções**.

2. Clique com o botão direito do mouse no **OrdersTableAdapter** e selecione **Adicionar Consulta**.

3. Deixe a opção padrão **Usar instruções SQL** e clique em **Avançar**.

4. Deixe a opção padrão **SELECT que retorna linhas** e clique em **Avançar**.

5. Adicione uma cláusula WHERE à consulta para retornar `Orders` com base no `CustomerID`. A consulta deve ser semelhante ao seguinte:

    ```
    SELECT OrderID, CustomerID, EmployeeID, OrderDate, RequiredDate, ShippedDate, ShipVia, Freight, ShipName, ShipAddress, ShipCity, ShipRegion, ShipPostalCode, ShipCountry
    FROM Orders
    WHERE CustomerID = @CustomerID
    ```

    > [!NOTE]
    > Verifique a sintaxe de parâmetro correta para o seu banco de dados. Por exemplo, no Microsoft Access, a cláusula WHERE seria algo como: `WHERE CustomerID = ?`.

6. Clique em **Avançar**.

7. Para obter **um nome de DataTableMethod de preenchimento**, digite `FillByCustomerID`.

8. Desmarque a opção **Retornar uma DataTable** e clique em **Avançar**.

9. Clique em **Finalizar**.

## <a name="create-a-method-on-form2-to-pass-data-to"></a>Criar um método no Form2 para passar dados para

#### <a name="to-create-a-method-to-pass-data-to"></a>Para criar um método para o qual passar dados

1. Clique com o botão direito do mouse no **Form2** e selecione **Exibir Código** para abrir o **Form2** no **Editor de Códigos**.

2. Adicione o seguinte código ao **Form2** depois do método `Form2_Load`:

     [!code-csharp[VbRaddataDisplaying#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form2.cs#1)]
     [!code-vb[VbRaddataDisplaying#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form2.vb#1)]

## <a name="create-a-method-on-form1-to-pass-data-and-display-form2"></a>Criar um método no Form1 para passar dados e exibir o Form2

#### <a name="to-create-a-method-to-pass-data-to-form2"></a>Para criar um método para passar dados para o Form2

1. No **Form1**, clique com o botão direito do mouse na grade de dados do Cliente e clique em **Propriedades**.

2. Na janela **Propriedades**, clique em **Eventos**.

3. Clique duas vezes no evento **CellDoubleClick**.

     O Editor de Códigos é exibido.

4. Atualize a definição de método para corresponder ao seguinte exemplo:

     [!code-csharp[VbRaddataDisplaying#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#2)]
     [!code-vb[VbRaddataDisplaying#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#2)]

## <a name="run-the-application"></a>Executar o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

- Pressione F5 para executar o aplicativo.

- Clique duas vezes em um registro de cliente no **Form1** para abrir o **Form2** com pedidos do cliente.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos de aplicativo, existem várias etapas que você talvez queira realizar após passar dados entre formulários. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

- Editar o conjunto de dados, para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Adicionar funcionalidade para salvar dados de volta no banco de dados. Para obter mais informações, consulte [salvar dados de volta no banco de dado](../data-tools/save-data-back-to-the-database.md).

## <a name="see-also"></a>Consulte também
 [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
