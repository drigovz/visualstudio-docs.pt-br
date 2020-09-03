---
title: Salvar dados em um banco de dado (várias tabelas) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72655456"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvar dados em um banco de dados (várias tabelas)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um dos cenários mais comuns no desenvolvimento de aplicativos é exibir dados de um formulário em um aplicativo do Windows, editar e enviá-los atualizados de volta para o banco de dados. Essa explicação passo a passo cria um formulário que exibe dados de duas tabelas relacionadas e mostra como editar registros e salvar alterações no banco de dados. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind.

 Você pode salvar os dados em seu aplicativo de volta no banco de dados chamando o método `Update` de um TableAdapter. Quando você arrasta tabelas da janela **fontes de dados** para um formulário, o código necessário para salvar os dados é adicionado automaticamente. Todas as tabelas adicionais que são adicionadas a um formulário exigem a adição manual desse código. Essa explicação passo a passo mostra como adicionar código para salvar atualizações de mais de uma tabela.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes daqueles descritos na ajuda, dependendo das configurações ativas ou da edição que você está usando. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 As tarefas ilustradas neste passo a passo incluem:

- Criando um novo projeto de **aplicativo do Windows** .

- Criando e configurando uma fonte de dados em seu aplicativo com o [Assistente de configuração de fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Definindo os controles dos itens na [janela fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Para obter mais informações, consulte [definir o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Criando controles associados a dados arrastando itens da janela **Fontes de Dados** para o formulário.

- Modificar alguns registros em cada tabela no conjunto de recursos.

- Modificando o código para enviar os dados atualizados no conjunto de dados de volta ao banco de dados.

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind.

## <a name="create-the-windows-application"></a>Criar o aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**. A atribuição de um nome ao projeto é opcional durante essa etapa, mas vamos dar um nome a ele porque estamos planejando salvá-lo mais tarde.

#### <a name="to-create-the-new-windows-application-project"></a>Para criar o novo projeto de aplicativo do Windows

1. No menu **arquivo** , crie um novo projeto.

2. Dê ao projeto o nome de `UpdateMultipleTablesWalkthrough`.

3. Selecione **aplicativo do Windows**e, em seguida, selecione **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **UpdateMultipleTablesWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="create-the-data-source"></a>Criar a fonte de dados
 Esta etapa cria uma fonte de dados com base em um banco de dados Northwind usando o **Assistente de Configuração de Fonte de Dados**. É preciso ter acesso ao banco de dados de exemplo Northwind para criar a conexão.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **dados** , selecione**mostrar fontes de dados**.

2. Na janela **fontes de dados** , selecione**Adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.

3. Na tela **escolher um tipo de fonte de dados**, selecione **banco**de dado e, em seguida, selecione **Avançar**.

4. Na tela **escolher sua conexão de dados**, siga um destes procedimentos:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

         - ou -

    - Selecione **Nova Conexão** para abrir a caixa de diálogo **Adicionar/Modificar Conexão**.

5. Se o seu banco de dados exigir uma senha, selecione a opção para incluir um dado confidencial e, em seguida, selecione **Avançar**.

6. Na **cadeia de conexão salvar no arquivo de configuração do aplicativo**, selecione **Avançar**.

7. Na tela **escolher seus objetos de banco de dados**, expanda o nó **tabelas** .

8. Selecione as tabelas **Customers** e **Orders** e, em seguida, selecione **Finish**.

     O **NorthwindDataSet** é adicionado ao projeto e as tabelas são exibidas na janela **Fontes de Dados**.

## <a name="set-the-controls-to-be-created"></a>Definir os controles a serem criados
 Para esta explicação, os dados na `Customers` tabela estão em um layout de **detalhes** em que os dados são exibidos em controles individuais. Os dados da `Orders` tabela estão em um layout de **grade** que é exibido em um <xref:System.Windows.Forms.DataGridView> controle.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Definir o tipo de remoção dos itens na Janela Fontes de Dados

1. Na janela **fontes de dados** , expanda o nó **clientes** .

2. No nó **clientes** , selecione **detalhes** na lista de controles para alterar o controle da tabela **Customers** para controles individuais. Para obter mais informações, consulte [definir o controle a ser criado ao arrastar da janela fontes de dados](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Criar o formulário associado a dados
 Você pode criar os controles associados a dados arrastando itens da janela **fontes de dados** para o formulário.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Para criar controles de associação de dados no formulário

1. Arraste o nó principal **Clientes** da janela **Fontes de Dados** para **Form1**.

     Os controles de associação de dados com rótulos descritivos são exibidos no formulário, juntamente com uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para registros de navegação. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

2. Arraste o nó **Ordens** relacionado da janela **Fontes de Dados** para **Form1**.

    > [!NOTE]
    > O nó **Ordens** relacionado está localizado abaixo da coluna **Fax** e é um nó filho do nó **Clientes**.

     Um controle <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource> aparece na bandeja do componente.

## <a name="addcode-to-update-the-database"></a>Addcode para atualizar o banco de dados
 É possível atualizar os bancos de dados chamando os métodos `Update` dos TableAdapters **Clientes** e **Ordens**. Por padrão, um manipulador de eventos para o botão **salvar** do <xref:System.Windows.Forms.BindingNavigator> é adicionado ao código do formulário para enviar atualizações para o banco de dados. Esse procedimento modifica o código para enviar atualizações na ordem correta. Isso elimina a possibilidade de gerar erros de integridade referencial. O código também implementa manipulação de erros com a quebra automática da chamada de atualização em um bloco try-catch. Você pode mudar o código para atender às necessidades do seu aplicativo.

> [!NOTE]
> Para maior clareza, este passo a passos não usa uma transação. No entanto, se você estiver atualizando duas ou mais tabelas relacionadas, inclua toda a lógica de atualização em uma transação. Uma transação é um processo que garante que todas as alterações relacionadas a um banco de dados sejam bem-sucedidas antes que as alterações sejam confirmadas. Para obter mais informações, consulte [Transações e simultaneidade](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Para adicionar lógica de atualização ao aplicativo

1. Selecione o botão **salvar** no <xref:System.Windows.Forms.BindingNavigator> . Isso abre o editor de código para o `bindingNavigatorSaveItem_Click` manipulador de eventos.

2. Substitua o código no manipulador de eventos para chamar os métodos `Update` dos TableAdapters relacionados. O código a seguir primeiro cria três tabelas de dados temporárias para armazenar as informações de cada <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>). Em seguida, as atualizações são executadas na ordem correta. O código deve se parecer com o seguinte:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Testar o aplicativo

#### <a name="to-test-the-application"></a>Para testar o aplicativo

1. Selecione **F5**.

2. Faça algumas alterações nos dados de um ou mais registros em cada tabela.

3. Selecione o botão **Salvar**.

4. Confira os valores no banco de dados para verificar se as alterações foram salvas.

## <a name="next-steps"></a>Próximas etapas
 Dependendo dos requisitos do aplicativo, há várias etapas que você pode querer executar depois de criar um formulário associado a dados em seu aplicativo do Windows. Entre algumas das melhorias que você poderia fazer nessa explicação passo a passo estão:

- Adicionando funcionalidade de busca ao formulário. Para obter mais informações, consulte [como: adicionar uma consulta parametrizada a um aplicativo Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Editando a fonte de dados para adicionar ou remover objetos de banco de dados. Para obter mais informações, consulte [como: editar um conjunto de](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3)dados.

## <a name="see-also"></a>Consulte Também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
