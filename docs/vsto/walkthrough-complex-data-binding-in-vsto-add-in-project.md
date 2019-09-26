---
title: 'Passo a passo: Associação de dados complexa no projeto de suplemento do VSTO'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], Excel
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: efe99e4d12ea4ace6d6c996b816dc315c502fa47
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255558"
---
# <a name="walkthrough-complex-data-binding-in-vsto-add-in-project"></a>Passo a passo: Associação de dados complexa no projeto de suplemento do VSTO
  Você pode associar dados a controles de host e controles de Windows Forms em projetos de suplemento do VSTO. Este tutorial demonstra como adicionar controles a uma Microsoft Office planilha do Excel e associar os controles aos dados em tempo de execução.

 [!INCLUDE[appliesto_xlallapp](../vsto/includes/appliesto-xlallapp-md.md)]

 Esta explicação passo a passo ilustra as seguintes tarefas:

- Adicionar um <xref:Microsoft.Office.Tools.Excel.ListObject> controle a uma planilha em tempo de execução.

- Criar um <xref:System.Windows.Forms.BindingSource> que conecta o controle a uma instância de um DataSet.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Pré-requisitos
 Você precisa dos seguintes componentes para concluir esta instrução passo a passo:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] ou [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Acesso a uma instância em execução do SQL Server 2005 ou SQL Server 2005 Express que tem `AdventureWorksLT` o banco de dados de exemplo anexado a ele. Você pode baixar o `AdventureWorksLT` banco de dados do [site do CodePlex](http://go.microsoft.com/fwlink/?LinkId=115611). Para obter mais informações sobre como anexar um banco de dados, consulte os seguintes tópicos:

  - Para anexar um banco de dados usando SQL Server Management Studio ou SQL Server Management Studio Express, [consulte Como: Anexar um banco de dados (](/sql/relational-databases/databases/attach-a-database)SQL Server Management Studio).

  - Para anexar um banco de dados usando a linha de comando [, consulte Como: Anexe um arquivo de banco de](/previous-versions/sql/)dados a SQL Server Express.

## <a name="create-a-new-project"></a>Criar um novo projeto
 A primeira etapa é criar um projeto de suplemento do VSTO do Excel.

### <a name="to-create-a-new-project"></a>Para criar um novo projeto

1. Crie um projeto de suplemento do VSTO do Excel com o nome **populando planilhas de um banco de dados**, usando Visual Basic ou C#.

     Para obter mais informações, confira [Como: Crie projetos do Office no Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

     O Visual Studio abre `ThisAddIn.vb` o `ThisAddIn.cs` arquivo ou e adiciona as **planilhas populando de um** projeto de banco de dados para **Gerenciador de soluções**.

## <a name="create-a-data-source"></a>Criar uma fonte de dados
 Use a janela **Data Sources** para adicionar um conjunto de dados tipado ao seu projeto.

### <a name="to-add-a-typed-dataset-to-the-project"></a>Para adicionar um conjunto de um dataset tipado ao projeto

1. Se a **janela fontes de dados** não estiver visível, exiba-a por, na barra de menus, escolhendo **Exibir** > outras**fontes de dados**do**Windows** > .

2. Escolha **Adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.

3. Clique em **banco de dados**e em **Avançar**.

4. Se você tiver uma conexão existente com o `AdventureWorksLT` banco de dados, escolha essa conexão e clique em **Avançar**.

    Caso contrário, clique em **nova conexão**e use a caixa de diálogo **Adicionar conexão** para criar a nova conexão. Para obter mais informações, consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

5. Na página **salvar a cadeia de conexão no arquivo de configuração do aplicativo** , clique em **Avançar**.

6. Na página **escolher seus objetos de banco de dados** , expanda **tabelas** e selecione **Endereço (tabela SalesLT)** .

7. Clique em **Finalizar**.

    O arquivo *AdventureWorksLTDataSet. xsd* é adicionado ao **Gerenciador de soluções**. Esse arquivo define os seguintes itens:

   - Um dataset tipado `AdventureWorksLTDataSet`chamado. Esse DataSet representa o conteúdo da tabela **Address (tabela SalesLT)** no banco de dados AdventureWorksLT.

   - Um TableAdapter chamado `AddressTableAdapter`. Esse TableAdapter pode ser usado para ler e gravar dados no `AdventureWorksLTDataSet`. Para obter mais informações, consulte [visão geral do TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Você usará esses dois objetos posteriormente neste passo a passos.

## <a name="create-controls-and-bind-controls-to-data"></a>Criar controles e associar controles a dados
 Para este guia, o <xref:Microsoft.Office.Tools.Excel.ListObject> controle exibe todos os dados na tabela que você selecionou assim que o usuário abre a pasta de trabalho. O objeto de lista usa <xref:System.Windows.Forms.BindingSource> um para conectar o controle ao banco de dados.

 Para obter mais informações sobre como ligar controles a dados, consulte [associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md).

### <a name="to-add-the-list-object-dataset-and-table-adapter"></a>Para adicionar o objeto de lista, conjunto de tabelas e adaptador de tabela

1. Na classe, declare os seguintes controles para exibir a `Address` tabela do `AdventureWorksLTDataSet` conjunto de um. `ThisAddIn`

     [!code-csharp[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_ExcelAddInDatabase#1](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#1)]

2. No método, adicione o código a seguir para inicializar o DataSet e preencher o conjunto de dados com as `AdventureWorksLTDataSet` informações do DataSet. `ThisAddIn_Startup`

     [!code-csharp[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#2)]
     [!code-vb[Trin_ExcelAddInDatabase#2](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#2)]

3. Adicione o seguinte código ao método de `ThisAddIn_Startup` . Isso gera um item de host que estende a planilha. Para obter mais informações, consulte [estender documentos do Word e pastas de trabalho do Excel em suplementos do VSTO em tempo de execução](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

     [!code-csharp[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#3)]
     [!code-vb[Trin_ExcelAddInDatabase#3](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#3)]

4. Crie um intervalo e adicione o <xref:Microsoft.Office.Tools.Excel.ListObject> controle.

     [!code-csharp[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#4)]
     [!code-vb[Trin_ExcelAddInDatabase#4](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#4)]

5. Associe o objeto de lista `AdventureWorksLTDataSet` ao usando o <xref:System.Windows.Forms.BindingSource>. Passe os nomes das colunas que você deseja associar ao objeto de lista.

     [!code-csharp[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/CSharp/Trin_ExcelAddInDatabase_O12/ThisAddIn.cs#5)]
     [!code-vb[Trin_ExcelAddInDatabase#5](../vsto/codesnippet/VisualBasic/Trin_ExcelAddInDatabase_O12/ThisAddIn.vb#5)]

## <a name="test-the-add-in"></a>Testar o suplemento
 Quando você abrir o Excel, <xref:Microsoft.Office.Tools.Excel.ListObject> o controle exibirá os dados `Address` da tabela do `AdventureWorksLTDataSet` DataSet.

### <a name="to-test-the-vsto-add-in"></a>Para testar o suplemento do VSTO

- Pressione **F5**.

     Um <xref:Microsoft.Office.Tools.Excel.ListObject> controle chamado `addressListObject` é criado na planilha. Ao mesmo tempo, um objeto DataSet chamado `adventureWorksLTDataSet` e um <xref:System.Windows.Forms.BindingSource> nomeado `addressBindingSource` são adicionados ao projeto. O <xref:Microsoft.Office.Tools.Excel.ListObject> é associado <xref:System.Windows.Forms.BindingSource>ao, que, por sua vez, é associado ao objeto DataSet.

## <a name="see-also"></a>Consulte também

- [Dados em soluções do Office](../vsto/data-in-office-solutions.md)
- [Associar dados a controles em soluções do Office](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Como: Preencher planilhas com dados de um banco de dado](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Como: Preencher documentos com dados de um banco de dado](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Como: Preencher documentos com dados de serviços](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Como: Preencher documentos com dados de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Como: Percorrer os registros de banco de dados em uma planilha](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Como: Atualizar uma fonte de dados com dados de um controle de host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Passo a passo: Vinculação de dados simples em um projeto de nível de documento](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)
- [Passo a passo: Ligação de dados complexa em um projeto de nível de documento](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)
- [Visão geral de usar arquivos de banco de dados local em soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)
- [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Visão geral de usar arquivos de banco de dados local em soluções do Office](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [Visão geral do componente BindingSource](/dotnet/framework/winforms/controls/bindingsource-component-overview)
