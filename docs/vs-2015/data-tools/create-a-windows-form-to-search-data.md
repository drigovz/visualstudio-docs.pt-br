---
title: Criar um formulário do Windows para pesquisar dados | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 81980f38cbd8fb595530cc52b2cf32056feb43a7
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670056"
---
# <a name="create-a-windows-form-to-search-data"></a>Criar um Windows Form para pesquisar dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um cenário de aplicativo comum exibirá dados selecionados em um formulário. Por exemplo, você pode querer exibir os pedidos de um cliente específico ou os detalhes de um pedido específico. Nesse cenário, um usuário insere informações em um formulário e uma consulta é executada com a entrada do usuário como parâmetro, ou seja, os dados são selecionados com base em uma consulta parametrizada. A consulta retorna apenas os dados que satisfazem os critérios inseridos pelo usuário. Este passo a passo mostra como criar uma consulta que retorna clientes de uma cidade específica, como mudar a interface do usuário para que os usuários possam inserir o nome de uma cidade e pressionar um botão para executar a consulta.

 O uso de consultas parametrizadas ajuda a tornar seu aplicativo eficiente, permitindo que o banco de dados funcione melhor, filtrando registros rapidamente. Por outro lado, se você solicitar uma tabela de banco de dados inteira, transferi-la pela rede e usar a lógica do aplicativo para encontrar os registros que deseja, o aplicativo poderá ficar lento e ineficiente.

 Você pode adicionar consultas parametrizadas a qualquer TableAdapter (e controles para aceitar valores de parâmetro e executar a consulta), usando a caixa de diálogo **search criteria Builder** . Abra a caixa de diálogo selecionando o comando **Adicionar Consulta** no menu **Dados** (ou em qualquer marcação inteligente de TableAdapter).

 As tarefas ilustradas neste passo a passo incluem:

- Criando um novo projeto de aplicativo Windows Forms.

- Criando e configurando a fonte de dados em seu aplicativo com o assistente de **configuração de fonte de dados** .

- Definindo o tipo de descartação dos itens na janela **fontes de dados** .

- Criar controles que exibem dados arrastando itens da janela **Fontes de Dados** para um formulário.

- Adicionar controles para exibir os dados no formulário.

- Concluindo a caixa de diálogo **Construtor de critérios de pesquisa** .

- Inserindo parâmetros no formulário e executando a consulta parametrizada.

## <a name="prerequisites"></a>Prerequisites
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-the-windows-application"></a>Criar o aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**. A atribuição de um nome ao projeto é opcional nesta etapa, mas você o atribuirá um nome aqui, pois você o salvará mais tarde.

#### <a name="to-create-the-new-windows-application-project"></a>Para criar o novo projeto de Aplicativo do Windows

1. No menu **arquivo** , crie um novo projeto.

2. Nomeie o projeto `WindowsSearchForm`.

3. Selecione **aplicativo do Windows** e clique em **OK**.

     O projeto **WindowsSearchForm** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="create-the-data-source"></a>Criar a fonte de dados
 Esta etapa cria uma fonte de dados usando o assistente de **configuração de fonte de dados** . É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão. Para obter informações sobre como configurar o banco de dados de exemplo Northwind, consulte [instalar SQL Server bancos](../data-tools/install-sql-server-sample-databases.md)de dados de exemplo.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **Dados**, clique em **Mostrar Fontes de Dados**.

2. Na janela **Fontes de Dados**, selecione **Adicionar Nova Fonte de Dados** para iniciar o assistente de **Configuração de Fonte de Dados**.

3. Selecione **Banco de Dados** na página **Escolher um Tipo de Fonte de Dados** e, em seguida, clique em **Avançar**.

4. Na página **Escolha a Conexão de Dados**, faça o seguinte:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

    - Selecione **Nova Conexão** para inicializar a caixa de diálogo **Adicionar/Modificar Conexão**.

5. Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **Avançar**.

6. Na página **salvar cadeia de conexão no arquivo de configuração do aplicativo** , clique em **Avançar**.

7. Na página **escolher seus objetos de banco de dados** , expanda o nó **tabelas** .

8. Selecione a tabela **Clientes** e clique em **Concluir**.

     O **NorthwindDataSet** é adicionado ao seu projeto e a tabela **Clientes** aparece na janela **Fontes de Dados**.

## <a name="create-the-form"></a>Criar o formulário
 Você pode criar controles de associação de dados arrastando itens da janela **Fontes de Dados** para um formulário.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

1. Expanda o nó **Clientes** na janela **Fontes de Dados**.

2. Arraste o nó **Clientes** da janela **Fontes de Dados** para o formulário.

     Um <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

## <a name="addparameterization-search-functionality-to-the-query"></a>Addparametrization (funcionalidade de pesquisa) para a consulta
 Você pode adicionar uma cláusula WHERE à consulta original usando a caixa de diálogo **Construtor de critérios de pesquisa** .

#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Para criar uma consulta parametrizada e controles para inserir os parâmetros

1. Selecione o controle <xref:System.Windows.Forms.DataGridView> e escolha **Adicionar Consulta** no menu **Dados**.

2. Digite `FillByCity` na área **nome da nova consulta** na caixa de diálogo **Construtor de critérios de pesquisa** .

3. Adicione `WHERE City = @City` à consulta na área **Texto da Consulta**.

     A consulta deve ser semelhante ao seguinte:

     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`

     `FROM Customers`

     `WHERE City = @City`

    > [!NOTE]
    > As fontes de dados Access e OLE DB usam o ponto de interrogação ('? ') para denotar parâmetros, portanto, a cláusula WHERE ficaria assim: `WHERE City = ?`.

4. Clique em **OK** para fechar a caixa de diálogo **Construtor de Critérios de Pesquisa**.

     Um **FillByCityToolStrip** é adicionado ao formulário.

## <a name="testing-the-application"></a>Testando o aplicativo
 A execução do aplicativo abre o formulário pronto para receber o parâmetro como entrada.

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Pressione F5 para executar o aplicativo.

2. Digite **Londres** na caixa de texto **Cidade** e clique em **FillByCity**.

     A grade de dados é populada com clientes que atendem aos critérios. Neste exemplo, a grade de dados exibe os clientes que têm o valor **Londres** na coluna **Cidade**.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos de aplicativo, existem várias etapas que você talvez queira realizar após criar um formulário parametrizado. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

- Adicionar controles que exibem dados relacionados.

- Editando o conjunto de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).

## <a name="see-also"></a>Consulte também
 [Associando controles do Windows Forms a dados no Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
