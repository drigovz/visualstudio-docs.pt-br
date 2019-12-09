---
title: 'Instruções passo a passo: criando um conjunto de dados com o Designer de Conjunto de Dados'
ms.date: 09/11/2017
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9b6c91e6074e34a8207325e25f4a48b94dd037ef
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72639437"
---
# <a name="walkthrough-create-a-dataset-with-the-dataset-designer"></a>Walkthrough: criar um conjunto de um DataSet com o Designer de Conjunto de Dados

Neste tutorial, você cria um conjunto de um DataSet usando o **Designer de conjunto de dados**. O artigo orienta você pelo processo de criação de um novo projeto e da adição de um novo item de **conjunto** de um. Você aprenderá a criar tabelas com base em tabelas em um banco de dados sem usar um assistente.

## <a name="prerequisites"></a>Prerequisites

Este passo a passos usa SQL Server Express LocalDB e o banco de dados de exemplo Northwind.

1. Se você não tiver SQL Server Express LocalDB, instale-o na [SQL Server Express página de download](https://www.microsoft.com/sql-server/sql-server-editions-express)ou por meio do **instalador do Visual Studio**. No Instalador do Visual Studio, o SQL Server Express LocalDB pode ser instalado como parte da carga de trabalho de **armazenamento e processamento de dados** ou como um componente individual.

2. Instale o banco de dados de exemplo Northwind seguindo estas etapas:

    1. No Visual Studio, abra a janela **pesquisador de objetos do SQL Server** . (O Pesquisador de Objetos do SQL Server é instalado como parte da carga de trabalho de **armazenamento e processamento de dados** no instalador do Visual Studio.) Expanda o nó **SQL Server** . Clique com o botão direito do mouse na instância do LocalDB e selecione **nova consulta**.

       Uma janela do editor de consultas é aberta.

    2. Copie o [script do Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) para a área de transferência. Esse script T-SQL cria o banco de dados Northwind a partir do zero e o preenche com os mesmos.

    3. Cole o script T-SQL no editor de consultas e, em seguida, escolha o botão **executar** .

       Após um curto período, a consulta conclui a execução e o banco de dados Northwind é criado.

## <a name="create-a-new-windows-forms-application-project"></a>Criar um novo projeto de aplicativo do Windows Forms

1. No Visual Studio, no menu **arquivo** , selecione **novo** **projeto**de  > .

2. Expanda **o C# Visual** ou **Visual Basic** no painel esquerdo e, em seguida, selecione **área de trabalho do Windows**.

3. No painel central, selecione o tipo de projeto **Windows Forms aplicativo** .

4. Nomeie o projeto **DatasetDesignerWalkthrough**e escolha **OK**.

     O Visual Studio adiciona o projeto para **Gerenciador de soluções** e exibe um novo formulário no designer.

## <a name="add-a-new-dataset-to-the-application"></a>Adicionar um novo conjunto de aplicativos ao aplicativo

1. No menu **Projeto**, selecione **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

2. No painel esquerdo, selecione **dados**e, em seguida, selecione **DataSet** no painel central.

3. Nomeie **o conjunto de DataSet e, em**seguida, escolha **Adicionar**.

     O Visual Studio adiciona um arquivo chamado **NorthwindDataSet. xsd** ao projeto e o abre no **Designer de conjunto de dados**.

## <a name="create-a-data-connection-in-server-explorer"></a>Criar uma conexão de dados no Gerenciador de Servidores

1. No menu **Exibir** , clique em **Gerenciador de servidores**.

2. Em **Gerenciador de servidores**, clique no botão **conectar ao banco de dados** .

3. Crie uma conexão com o banco de dados de exemplo Northwind.

## <a name="create-the-tables-in-the-dataset"></a>Criar as tabelas no conjunto de

Esta seção explica como adicionar tabelas ao conjunto de os.

### <a name="to-create-the-customers-table"></a>Para criar a tabela Customers

1. Expanda a conexão de dados que você criou em **Gerenciador de servidores**e, em seguida, expanda o nó **tabelas** .

2. Arraste a tabela **Customers** de **Gerenciador de Servidores** para a **Designer de conjunto de dados**.

     Uma tabela de dados **Customers** e **CustomersTableAdapter** são adicionadas ao DataSet.

### <a name="to-create-the-orders-table"></a>Para criar a tabela Orders

- Arraste a tabela **Orders** de **Gerenciador de Servidores** para a **Designer de conjunto de dados**.

     Uma tabela de dados **Orders** , **OrdersTableAdapter**e relação de dados entre as tabelas **Customers** e **Orders** são adicionadas ao DataSet.

### <a name="to-create-the-orderdetails-table"></a>Para criar a tabela OrderDetails

- Arraste a tabela **detalhes do pedido** de **Gerenciador de Servidores** para a **Designer de conjunto de dados**.

     Uma tabela de dados **detalhes do pedido** , **OrderDetailsTableAdapter**, e uma relação de dados entre as tabelas **pedidos** e **OrderDetails** são adicionadas ao DataSet.

## <a name="next-steps"></a>Próximas etapas

- Salve o conjunto de um.

- Selecione os itens na janela **fontes de dados** e arraste-os para um formulário. Para obter mais informações, consulte [associar controles de Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Adicione mais consultas aos TableAdapters.

- Adicione a lógica de validação para os eventos <xref:System.Data.DataTable.ColumnChanging> ou <xref:System.Data.DataTable.RowChanging> das tabelas de dados no DataSet. Para obter mais informações, consulte [Validate data in DataSets](../data-tools/validate-data-in-datasets.md).

## <a name="see-also"></a>Consulte também

- [Criar e configurar conjuntos de dados no Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Validar dados](../data-tools/validate-data-in-datasets.md)