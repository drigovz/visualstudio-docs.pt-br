---
title: Criar um controle de usuário Windows Forms que dá suporte à vinculação de dados de pesquisa | Microsoft Docs
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
- LookupBindingPropertiesAttribute class, examples
- user controls [Visual Basic], creating
ms.assetid: c48b4d75-ccfc-4950-8b14-ff8adbfe4208
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 48891f82667270f04af49c60122c63f8d3a943f7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668783"
---
# <a name="create-a-windows-forms-user-control-that-supports-lookup-data-binding"></a>Criar um controle de usuário do Windows Forms compatível com associação de dados de consulta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao exibir dados no Windows Forms, você poderá escolher os controles existentes da **Caixa de Ferramentas** ou criar controles personalizados se o aplicativo exigir alguma funcionalidade que não esteja disponível nos controles padrão. Este passo a passo mostra como criar um controle que implementa o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>. Os controles que implementam o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> contêm três propriedade que podem ser associadas a dados. Tais controles são semelhantes a um <xref:System.Windows.Forms.ComboBox>.

 Para obter mais informações sobre a criação de controles, consulte [desenvolvendo Windows Forms controles em tempo de design](https://msdn.microsoft.com/library/e5a8e088-7ec8-4fd9-bcb3-9078fd134829).

 Ao criar controles para uso em cenários de associação de dados, é necessário implementar um dos seguintes atributos de associação de dados:

|Uso de atributo de vinculação de dados|
|-----------------------------------|
|Implemente o <xref:System.ComponentModel.DefaultBindingPropertyAttribute> em controles simples, como um <xref:System.Windows.Forms.TextBox>, que exibe uma única coluna (ou propriedade) de dados. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à vinculação de dados simples](../data-tools/create-a-windows-forms-user-control-that-supports-simple-data-binding.md).|
|Implemente o <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.DataGridView> que exibe listas (ou tabelas) de dados. Para obter mais informações, consulte [criar um Windows Forms controle de usuário que dá suporte à ligação de dados complexa](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md).|
|Implemente o <xref:System.ComponentModel.LookupBindingPropertiesAttribute> nos controles, como um <xref:System.Windows.Forms.ComboBox>que exibe listas (ou tabelas) de dados, mas também precisa apresentar uma única coluna ou propriedade. (Esse processo é descrito nesta página de passo a passo.)|

 Este passo a passo cria um controle de pesquisa que se associa aos dados de duas tabelas. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind. O controle de pesquisa será associado ao campo `CustomerID` da tabela `Orders`. Ele usará este valor para pesquisar `CompanyName` na tabela `Customers`.

 Durante este passo a passo, você aprenderá a:

- Crie um novo **aplicativo do Windows**.

- Adicionar um novo **Controle de Usuário** ao projeto.

- Projetar visualmente o controle do usuário.

- Implementar o atributo `LookupBindingProperty`.

- Crie um conjunto de dados com o assistente de **configuração de fonte de dados** .

- Definir a coluna **CustomerID** na tabela **Pedidos** na janela **Fontes de Dados** para usar o novo controle.

- Criar um formulário para exibir dados no novo controle.

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-a-windows-application"></a>Criar um aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no menu **arquivo** , crie um novo **projeto**.

2. Nomeie o projeto **LookupControlWalkthrough**.

3. Selecione **Windows Forms aplicativo**e clique em **OK**.

     O projeto **LookupControlWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="add-a-user-control-to-the-project"></a>Adicionar um controle de usuário ao projeto
 Este passo a passo cria um controle de pesquisa de um **Controle de Usuário**, portanto, adicione um item de **Controle de Usuário** ao projeto **LookupControlWalkthrough**.

#### <a name="to-add-a-user-control-to-the-project"></a>Para adicionar um controle de usuário ao projeto

1. No menu **Projeto**, selecione **Adicionar Controle do Usuário**.

2. Digite `LookupBox` a área **nome** e clique em **Adicionar**.

     O controle **LookupBox** é adicionado ao **Gerenciador de Soluções** e abre no designer.

## <a name="design-the-lookupbox-control"></a>Criar o controle LookupBox

#### <a name="to-design-the-lookupbox-control"></a>Para projetar o controle LookupBox

- Arraste um <xref:System.Windows.Forms.ComboBox> da **Caixa de Ferramentas** para a superfície de design do controle de usuário.

## <a name="add-the-required-data-binding-attribute"></a>Adicionar o atributo de associação de dados necessário
 Para controles de pesquisa que suportam associação de dados, você pode implementar o <xref:System.ComponentModel.LookupBindingPropertiesAttribute>.

#### <a name="to-implement-the-lookupbindingproperties-attribute"></a>Para implementar o atributo LookupBindingProperties

1. Mude o controle **LookupBox** para exibição de código. (No menu **Exibir**, escolha **Código**.)

2. Substitua o código no `LookupBox` pelo seguinte:

     [!code-csharp[VbRaddataDisplaying#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/LookupBox.cs#5)]
     [!code-vb[VbRaddataDisplaying#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/LookupBox.vb#5)]

3. No menu **Compilar** , escolha **Compilar solução**.

## <a name="create-a-data-source-from-your-database"></a>Criar uma fonte de dados do seu banco de dados
 Esta etapa cria uma fonte de dados usando o **Assistente de Configuração de Fonte de Dados** com base nas tabelas `Customers` e `Orders` no banco de dados de exemplo Northwind. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [instalar SQL Server bancos](../data-tools/install-sql-server-sample-databases.md)de dados de exemplo.

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

8. Selecione as tabelas `Customers` e `Orders` e, em seguida, clique em **Concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e as `Customers` tabelas e `Orders` aparecem na janela **Data Sources** .

## <a name="set-the-customerid-column-of-the-orders-table-to-use-the-lookupbox-control"></a>Definir a coluna CustomerID da tabela Orders para usar o controle LookupBox
 Na janela **Fontes de Dados**, você pode definir o controle a ser criado antes de arrastar itens para seu formulário.

#### <a name="to-set-the-customerid-column-to-bind-to-the-lookupbox-control"></a>Para definir a coluna CustomerID para se associar ao controle LookupBox

1. Abra **Form1** no designer.

2. Expanda o nó **Clientes** na janela **Fontes de Dados**.

3. Expanda o nó **Pedidos** (no nó **Clientes** abaixo da coluna **Fax**).

4. Clique na seta suspensa no nó **Pedidos** e escolha **Detalhes** na lista de controle.

5. Clique na seta suspensa na coluna **CustomerID** (no nó **Pedidos**) e escolha **Personalizar**.

6. Selecione **LookupBox** na lista de **Controles Associados** na caixa de diálogo **Opções de Personalização da Interface do Usuário de Dados**.

7. Clique em **OK**.

8. Clique na seta suspensa na coluna **CustomerID** e escolha **LookupBox**.

## <a name="addcontrols-to-the-form"></a>Addcontroles para o formulário
 É possível criar controles de associação de dados ao arrastar itens da janela **Fontes de Dados** para **Form1**.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar controles de associação de dados no Windows Form

- Arraste o nó **pedidos** da janela **fontes de dados** para o Windows Form e verifique se o controle **LookupBox** é usado para exibir os dados na `CustomerID` coluna.

## <a name="bind-the-control-to-look-up-companyname-from-the-customers-table"></a>Associar o controle para procurar o CompanyName da tabela Customers

#### <a name="to-setup-the-lookup-bindings"></a>Para configurar associações de pesquisa

- Selecione o nó **clientes** principais na janela **fontes de dados** e arraste-o para a caixa de combinação no **CustomerIDLookupBox** no **Form1**.

     Isso configura a associação de dados para exibir o `CompanyName` da tabela `Customers` mantendo, ao mesmo tempo, o valor `CustomerID` da tabela `Orders`.

## <a name="running-the-application"></a>Executando o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

- Pressione F5 para executar o aplicativo.

- Navegue por alguns registros e verifique se `CompanyName` aparece no controle `LookupBox`.

## <a name="see-also"></a>Consulte Também
 [Associar controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
