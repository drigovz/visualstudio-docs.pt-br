---
title: Criar um controle de usuário Windows Forms que dá suporte à vinculação de dados complexa | Microsoft Docs
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
- data binding, user controls
- data binding, complex
- user controls [Visual Studio], complex data binding
ms.assetid: c8f29c2b-b49b-4618-88aa-33b6105880b5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 99c4a20939ed2e3a036831930749bb59b5a42315
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670048"
---
# <a name="create-a-windows-forms-user-control-that-supports-complex-data-binding"></a>Criar um controle de usuário do Windows Forms que dá suporte à vinculação de dados complexos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao exibir dados em formulários nos aplicativos do Windows, você poderá escolher os controles existentes da **Caixa de Ferramentas** ou criar controles personalizados se o aplicativo exigir alguma funcionalidade que não esteja disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> contêm uma propriedade de `DataSource` e `DataMember` que pode ser associada a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.DataGridView> ou <xref:System.Windows.Forms.ListBox>.

 Para obter mais informações sobre a criação de controles, consulte [desenvolvendo Windows Forms controles em tempo de design](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Ao criar controles para uso em cenários de associação de dados, é necessário implementar um dos seguintes atributos de associação de dados:

|Uso de atributo de vinculação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. (Esse processo é descrito nesta página de passo a passo.)|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).|

 Este passo a passo cria um controle complexo que exibe linhas de dados de uma tabela. Este exemplo usa a tabela `Customers` do banco de dados de exemplo Northwind. O controle de usuário complexo exibirá a tabela de clientes em uma <xref:System.Windows.Forms.DataGridView> no controle personalizado.

 Durante este passo a passo, você aprenderá a:

- Crie um novo **aplicativo do Windows**.

- Adicionar um novo **Controle de Usuário** ao projeto.

- Projetar visualmente o controle do usuário.

- Implementar o atributo `ComplexBindingProperty`.

- Crie um conjunto de dados com o [Assistente de configuração de fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Defina a tabela **Customers** na [janela Data Sources](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para usar o novo controle complexo.

- Adicione o novo controle arrastando-o da **janela Data Sources** para o **Form1**.

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-a-windows-application"></a>Criar um aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no menu **arquivo** , crie um novo **projeto**.

2. Nomeie o projeto como **ComplexControlWalkthrough**.

3. Selecione **aplicativo do Windows**e clique em **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **ComplexControlWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto
 Como este passo a passos cria um controle vinculável de dados complexo de um **controle de usuário**, você deve adicionar um item de **controle de usuário** ao projeto.

#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1. No menu **Projeto**, escolha **Adicionar Controle do Usuário**.

2. Digite **ComplexDataGridView** na área **Nome** e clique em **Adicionar**.

     O controle **ComplexDataGridView** é adicionado ao **Gerenciador de Soluções** e abre no designer.

## <a name="design-the-complexdatagridview-control"></a>Criar o controle ComplexDataGridView
 Esta etapa adiciona um <xref:System.Windows.Forms.DataGridView> ao controle de usuário.

#### <a name="to-design-the-complexdatagridview-control"></a>Para projetar o controle ComplexDataGridView

- Arraste um <xref:System.Windows.Forms.DataGridView> da **Caixa de Ferramentas** para a superfície de design do controle de usuário.

## <a name="add-the-required-data-binding-attribute"></a>Adicionar o atributo de associação de dados necessário
 Para controles complexos que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute>.

#### <a name="to-implement-the-complexbindingproperties-attribute"></a>Para implementar o atributo ComplexBindingProperties

1. Alterne o controle **ComplexDataGridView** para exibição de código. (No menu **Exibir**, selecione **Código**.)

2. Substitua o código no `ComplexDataGridView` pelo seguinte:

     [!code-csharp[VbRaddataDisplaying#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/ComplexDataGridView.cs#4)]
     [!code-vb[VbRaddataDisplaying#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/ComplexDataGridView.vb#4)]

3. No menu **Compilar** , escolha **Compilar solução**.

## <a name="creating-a-data-source-from-your-database"></a>Criando uma fonte de dados do seu banco de dados
 Esta etapa usa o assistente de **configuração de fonte de dados** para criar uma fonte de dados com base na `Customers` tabela no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [instalar SQL Server bancos](../data-tools/install-sql-server-sample-databases.md)de dados de exemplo.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

2. Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o assistente de **Configuração de Fonte de Dados**.

3. Selecione **Banco de Dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, clique em **Avançar**.

4. Na página **escolher sua conexão de dados** , siga um destes procedimentos:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **Nova Conexão** para inicializar a caixa de diálogo **Adicionar/Modificar Conexão**.

5. Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Avançar**.

6. Na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** , clique em **Avançar**.

7. Na página **escolher seus objetos de banco de dados** , expanda o nó **tabelas** .

8. Selecione a tabela `Customers` e clique em **Concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e a `Customers` tabela é exibida na janela **Data Sources** .

## <a name="set-the-customers-table-to-use-the-complexdatagridview-control"></a>Definir a tabela Customers para usar o controle ComplexDataGridView
 Na janela **Fontes de Dados**, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

#### <a name="to-set-the-customers-table-to-bind-to-the-complexdatagridview-control"></a>Para configurar a coluna Clientes para se associar ao controle ComplexDataGridView

1. Abra **Form1** no designer.

2. Expanda o nó **Clientes** na janela **Fontes de Dados**.

3. Clique na seta suspensa no nó **Clientes** e escolha **Personalizar**.

4. Selecione **ComplexDataGridView** na lista de **Controles Associados** na caixa de diálogo **Opções de Personalização da Interface do Usuário de Dados**.

5. Clique na seta suspensa na tabela `Customers` e escolha **ComplexDataGridView** na lista de controle.

## <a name="addcontrols-to-the-form"></a>Addcontroles para o formulário
 Você pode criar os controles associados a dados arrastando itens da janela **fontes de dados** para o formulário.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

- Arraste o nó **clientes** principais da janela **fontes de dados** para o formulário. Verifique se o controle **ComplexDataGridView** é usado para exibir os dados da tabela.

## <a name="running-the-application"></a>Executando o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

- Pressione F5 para executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos do aplicativo, existem várias etapas que você pode realizar após criar um controle com suporte a associação de dados. Algumas etapas seguintes típicas incluem:

- Colocando os controles personalizados em uma biblioteca de controles para que você possa reutilizá-los em outros aplicativos.

- Criando controles que suportam cenários de pesquisa. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados de pesquisa](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md).

## <a name="see-also"></a>Consulte Também
 [Associar controles de Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [defina o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md) [Windows Forms controles](https://msdn.microsoft.com/library/f050de8f-4ebd-4042-94b8-edf9a1dbd52a)
