---
title: Salvar dados em uma transação | Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671084"
---
# <a name="save-data-in-a-transaction"></a>Salvando dados em uma transação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tutorial demonstra como salvar dados em uma transação usando o <xref:System.Transactions> namespace. Este exemplo usa as tabelas `Customers` e `Orders` do banco de dados de exemplo Northwind.

## <a name="prerequisites"></a>Pré-requisitos
 Este passo a passo requer acesso ao banco de dados de exemplo Northwind.

## <a name="create-a-windows-application"></a>Criar um aplicativo do Windows
 A primeira etapa é criar um **aplicativo do Windows**.

#### <a name="to-create-the-new-windows-project"></a>Para criar o novo projeto do Windows

1. No Visual Studio, no menu **arquivo** , crie um novo **projeto**.

2. Nomeie o projeto **SavingDataInATransactionWalkthrough**.

3. Selecione **aplicativo do Windows**e, em seguida, selecione **OK**. Para obter mais informações, consulte [aplicativos cliente](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     O projeto **SavingDataInATransactionWalkthrough** é criado e adicionado ao **Gerenciador de Soluções**.

## <a name="create-a-database-data-source"></a>Criar uma fonte de dados de banco
 Esta etapa usa o [Assistente de configuração de fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) para criar uma fonte de dados com base nas `Customers` `Orders` tabelas e no banco de dados de exemplo Northwind.

#### <a name="to-create-the-data-source"></a>Para criar a fonte de dados

1. No menu **dados** , selecione**mostrar fontes de dados**.

2. Na janela **fontes de dados** , selecione **Adicionar nova fonte de dados** para iniciar o **Assistente de configuração de fonte de dados**.

3. Na tela **escolher um tipo de fonte de dados**, selecione **banco**de dado e, em seguida, selecione **Avançar**.

4. Na tela **escolher sua conexão de dados**, siga um destes procedimentos:

    - Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, selecione-o.

         - ou -

    - Selecione **Nova Conexão** para inicializar a caixa de diálogo **Adicionar/Modificar Conexão** e criar uma conexão com o banco de dados Northwind.

5. Se o seu banco de dados exigir uma senha, selecione a opção para incluir um dado confidencial e, em seguida, selecione **Avançar**.

6. Na tela **salvar cadeia de conexão no arquivo de configuração do aplicativo** , selecione **Avançar**.

7. Na tela **escolher seus objetos de banco de dados** , expanda o nó **tabelas** .

8. Selecione as `Customers` tabelas e e `Orders` , em seguida, selecione **concluir**.

     O **NorthwindDataSet** é adicionado ao projeto e as tabelas `Customers` e `Orders` aparecem na janela **Fontes de Dados**.

## <a name="addcontrols-to-the-form"></a>Addcontroles para o formulário
 Você pode criar os controles associados a dados arrastando itens da janela **fontes de dados** para o formulário.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Para criar controles associados a dados no Windows Form

- Na janela **fontes de dados** , expanda o nó **clientes** .

- Arraste o nó principal **Clientes** da janela **Fontes de Dados** para **Form1**.

     Um controle <xref:System.Windows.Forms.DataGridView> e uma faixa de ferramentas (<xref:System.Windows.Forms.BindingNavigator>) para navegação em registros são exibidos no formulário. Um [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> são exibidos na bandeja de componentes.

- Arraste o nó **pedidos** relacionados (não o nó **pedidos** principais, mas o nó de tabela filho relacionado abaixo da coluna **fax** ) no formulário abaixo do **customersDataGridView**.

     Um <xref:System.Windows.Forms.DataGridView> aparece no formulário. Um OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource> aparece na bandeja do componente.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Adicionar uma referência ao assembly System. Transactions
 As transações usam o namespace <xref:System.Transactions>. Uma referência de projeto para o assembly System. Transactions não é adicionada por padrão, portanto, você precisa adicioná-la manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Para adicionar uma referência ao arquivo DLL System.Transactions

1. No menu **projeto** , selecione**Adicionar referência**.

2. Selecione **System. Transactions**(na guia **.net** ) e, em seguida, selecione **OK**.

     Uma referência a **System.Transactions** é adicionada ao projeto.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Modifythe o código no botão SaveItem do BindingNavigator
 Para a primeira tabela descartada em seu formulário, o código é adicionado por padrão ao `click` evento do botão salvar no <xref:System.Windows.Forms.BindingNavigator> . É necessário adicionar manualmente o código para atualizar quaisquer tabelas adicionais. Para esta explicação, refatoro o código de salvamento existente do manipulador de eventos de clique do botão salvar. Também criamos mais alguns métodos para fornecer uma funcionalidade de atualização específica com base em se a linha precisa ser adicionada ou excluída.

#### <a name="to-modify-the-auto-generated-save-code"></a>Para modificar o código salvar gerado automaticamente

1. Selecione o botão **salvar** no **CustomersBindingNavigator** (o botão com o ícone de disquete).

2. Substitua o método `CustomersBindingNavigatorSaveItem_Click` pelo seguinte código:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   A ordem para reconciliar as alterações aos dados relacionados é a seguinte:

- Excluir registros filho. (Nesse caso, exclua os registros da `Orders` tabela.)

- Excluir registros pai. (Nesse caso, exclua os registros da `Customers` tabela.)

- Inserir registros pai. (Nesse caso, insira registros na `Customers` tabela.)

- Inserir registros filho. (Nesse caso, insira registros na `Orders` tabela.)

#### <a name="to-delete-existing-orders"></a>Para excluir pedidos existentes

- Adicione o seguinte método `DeleteOrders` a **Form1**:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Para excluir clientes existentes

- Adicione o seguinte método `DeleteCustomers` a **Form1**:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Para adicionar novos clientes

- Adicione o seguinte método `AddNewCustomers` a **Form1**:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Para adicionar novos pedidos

- Adicione o seguinte método `AddNewOrders` a **Form1**:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Executar o aplicativo

#### <a name="to-run-the-application"></a>Para executar o aplicativo

- Selecione **F5** para executar o aplicativo.

## <a name="see-also"></a>Consulte Também
 [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)
