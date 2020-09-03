---
title: Manipular uma exceção de simultaneidade | Microsoft Docs
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
- concurrency control, exceptions
- datasets [Visual Basic], errors
- exception handling, concurrency issues
- data concurrency, walkthroughs
- updating datasets, errors
- concurrency control, walkthroughs
ms.assetid: 73ee9759-0a90-48a9-bf7b-9d6fc17bff93
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1b3f9bdaf5107f805100b938212128d42c0263dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670031"
---
# <a name="handle-a-concurrency-exception"></a>Tratar uma exceção de simultaneidade
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As exceções de simultaneidade ( <xref:System.Data.DBConcurrencyException> ) são geradas quando dois usuários tentam alterar os mesmos dados em um banco de dado ao mesmo tempo. Neste tutorial, você cria um aplicativo do Windows que ilustra como pegar um <xref:System.Data.DBConcurrencyException> , localizar a linha que causou o erro e aprender uma estratégia de como tratá-lo.

 Este passo a passos percorre o seguinte processo:

1. Crie um novo projeto de **aplicativo do Windows** .

2. Crie um novo DataSet com base na `Customers` tabela Northwind.

3. Crie um formulário com um <xref:System.Windows.Forms.DataGridView> para exibir os dados.

4. Preencha um DataSet com dados da `Customers` tabela no banco de dados Northwind.

5. Use as [ferramentas de banco de dados Visual](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) no Visual Studio para acessar diretamente a `Customers` tabela de dados e alterar um registro.

6. Altere o mesmo registro para um valor diferente, atualize o conjunto de dados e tente gravar as alterações no banco de dados, o que resulta em um erro de simultaneidade sendo gerado.

7. Capture o erro e exiba as diferentes versões do registro, permitindo que o usuário determine se deseja continuar e atualizar o banco de dados ou para cancelar a atualização.

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passo, você precisará de:

- Acesso ao banco de dados de exemplo Northwind com permissão para executar atualizações.

> [!NOTE]
> As caixas de diálogo e os comandos de menu que você vê podem ser diferentes daqueles descritos na ajuda, dependendo das configurações ativas ou da edição que você está usando. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Criar um novo projeto
 Você começa seu passo a passos criando um novo aplicativo do Windows.

#### <a name="to-create-a-new-windows-application-project"></a>Para criar um novo projeto de aplicativo do Windows

1. No menu **arquivo** , crie um novo projeto.

2. No painel **tipos de projeto** , selecione uma linguagem de programação.

3. No painel **Modelos**, selecione **Aplicativos do Windows**.

4. Nomeie o projeto `ConcurrencyWalkthrough` e, em seguida, selecione **OK**.

     O Visual Studio adiciona o projeto para **Gerenciador de soluções** e exibe um novo formulário no designer.

## <a name="create-the-northwind-dataset"></a>Criar o conjunto de conjuntos Northwind
 Nesta seção, você criará um conjunto de um DataSet chamado `NorthwindDataSet` .

#### <a name="to-create-the-northwinddataset"></a>Para criar o NorthwindDataSet

1. No menu **dados** , escolha **Adicionar nova fonte de dados**.

     O [Assistente de configuração de fonte de dados](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) é aberto.

2. Na tela **escolher um tipo de fonte de dados**, selecione **Database**.

3. Selecione uma conexão com o banco de dados de exemplo Northwind na lista de conexões disponíveis. Se a conexão não estiver disponível na lista de conexões, selecione**nova conexão**

    > [!NOTE]
    > Se você estiver se conectando a um arquivo de banco de dados local, selecione **não** quando for perguntado se você deseja adicionar o arquivo ao seu projeto.

4. Na tela **salvar cadeia de conexão no arquivo de configuração do aplicativo**, selecione **Avançar**.

5. Expanda o nó **tabelas** e selecione a `Customers` tabela. O nome padrão do conjunto de um deve ser `NorthwindDataSet` .

6. Selecione **concluir** para adicionar o conjunto de os ao projeto.

## <a name="create-a-data-bound-datagridview-control"></a>Criar um controle DataGridView associado a dados
 Nesta seção, você cria um <xref:System.Windows.Forms.DataGridView> arrastando o item **clientes** da janela **fontes de dados** para seu formulário do Windows.

#### <a name="to-create-a-datagridview-control-that-is-bound-to-the-customers-table"></a>Para criar um controle DataGridView associado à tabela Customers

1. No menu **dados** , escolha **mostrar fontes de dados** para abrir a **janela fontes de dados**.

2. Na janela **fontes de dados** , expanda o nó **NorthwindDataSet** e selecione a tabela **Customers** .

3. Selecione a seta para baixo no nó da tabela e, em seguida, selecione **DataGridView** na lista suspensa.

4. Arraste a tabela para uma área vazia do formulário.

     Um <xref:System.Windows.Forms.DataGridView> controle chamado `CustomersDataGridView` e um <xref:System.Windows.Forms.BindingNavigator> nomeado `CustomersBindingNavigator` são adicionados ao formulário associado ao <xref:System.Windows.Forms.BindingSource> . Isso, no, é ligado associado à `Customers` tabela no `NorthwindDataSet` .

## <a name="test-the-form"></a>Testar o formulário
 Agora você pode testar o formulário para certificar-se de que ele se comporta conforme o esperado até este ponto.

#### <a name="to-test-the-form"></a>Para testar o formulário

1. Selecione **F5** para executar o aplicativo

     O formulário é exibido com um <xref:System.Windows.Forms.DataGridView> controle que é preenchido com dados da `Customers` tabela.

2. No menu **depurar** , selecione**parar depuração**.

## <a name="handleconcurrency-errors"></a>Erros de Handleconcurrency
 A maneira como você lida com erros depende das regras de negócios específicas que regem seu aplicativo. Para esta explicação, usamos a estratégia a seguir como um exemplo de como tratar o erro de simultaneidade.

 O applicationpresents o usuário com três versões do registro:

- O registro atual no banco de dados

- O registro original que é carregado no conjunto de registros

- As alterações propostas no conjunto de

  Em seguida, o usuário pode substituir o banco de dados pela versão proposta ou cancelar a atualização e atualizar o DataSet com os novos valores do banco de dados.

#### <a name="to-enable-the-handling-of-concurrency-errors"></a>Para habilitar o tratamento de erros de simultaneidade

1. Crie um manipulador de erro personalizado.

2. Exibe as opções para o usuário.

3. Processar a resposta do usuário.

4. Reenvie a atualização ou redefina os dados no DataSet.

### <a name="addcode-to-handle-the-concurrency-exception"></a>Addcode para manipular a exceção de simultaneidade
 Quando você tenta executar uma atualização e uma exceção é gerada, geralmente você deseja fazer algo com as informações fornecidas pela exceção gerada.

 Nesta seção, você adiciona o código que tenta atualizar o banco de dados. Você também lida com qualquer um <xref:System.Data.DBConcurrencyException> que possa ser gerado, bem como outras exceções.

> [!NOTE]
> Os `CreateMessage` `ProcessDialogResults` métodos e serão adicionados posteriormente neste passo a passos.

##### <a name="to-add-error-handling-for-the-concurrency-error"></a>Para adicionar tratamento de erro para o erro de simultaneidade

1. Adicione o seguinte código abaixo do `Form1_Load` método:

     [!code-csharp[VbRaddataConcurrency#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#1)]
     [!code-vb[VbRaddataConcurrency#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#1)]

2. Substitua o `CustomersBindingNavigatorSaveItem_Click` método para chamar o `UpdateDatabase` método para que fique semelhante ao seguinte:

     [!code-csharp[VbRaddataConcurrency#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#2)]
     [!code-vb[VbRaddataConcurrency#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#2)]

### <a name="displaychoices-to-the-user"></a>Displaychoices ao usuário
 O código que você acabou de escrever chama o `CreateMessage` procedimento para exibir informações de erro para o usuário. Para esta explicação, você usa uma caixa de mensagem para exibir as diferentes versões do registro para o usuário. Isso permite que o usuário escolha se deseja substituir o registro com as alterações ou cancelar a edição. Quando o usuário seleciona uma opção (clica em um botão) na caixa de mensagem, a resposta é passada para o `ProcessDialogResult` método.

##### <a name="to-create-the-message-to-display-to-the-user"></a>Para criar a mensagem a ser exibida para o usuário

- Crie a mensagem adicionando o código a seguir ao **Editor de código**. Insira este código abaixo do `UpdateDatabase` método.

     [!code-csharp[VbRaddataConcurrency#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#4)]
     [!code-vb[VbRaddataConcurrency#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#4)]

### <a name="process-the-users-response"></a>Processar a resposta do usuário
 Você também precisa de código para processar a resposta do usuário para a caixa de mensagem. As opções são substituir o registro atual no banco de dados pela alteração proposta, ou abandonar as alterações locais e atualizar a tabela data com o registro que está atualmente no banco de dado. Se o usuário escolher Sim, o <xref:System.Data.DataTable.Merge%2A> método será chamado com o argumento *PreserveChanges* definido como `true` . Isso faz com que a tentativa de atualização seja bem-sucedida, porque a versão original do registro agora corresponde ao registro no banco de dados.

##### <a name="to-process-the-user-input-from-the-message-box"></a>Para processar a entrada do usuário na caixa de mensagem

- Adicione o código a seguir abaixo do código que foi adicionado na seção anterior.

     [!code-csharp[VbRaddataConcurrency#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataConcurrency/CS/Form1.cs#3)]
     [!code-vb[VbRaddataConcurrency#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataConcurrency/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Testar o formulário
 Agora, é possível testar o formulário para garantir que ele se comporta da forma esperada. Para simular uma violação de simultaneidade, você precisa alterar os dados no banco de dados depois de preencher o NorthwindDataSet.

#### <a name="to-test-the-form"></a>Para testar o formulário

1. Selecione **F5** para executar o aplicativo.

2. Depois que o formulário for exibido, deixe-o em execução e alterne para o IDE do Visual Studio.

3. No menu **Exibir**, escolha **Gerenciador de Servidores**.

4. Em **Gerenciador de servidores**, expanda a conexão que seu aplicativo está usando e, em seguida, expanda o nó **tabelas** .

5. Clique com o botão direito do mouse na tabela **clientes** e selecione **Mostrar dados da tabela**.

6. No primeiro registro ( `ALFKI` ), altere `ContactName` para `Maria Anders2` .

    > [!NOTE]
    > Navegue até uma linha diferente para confirmar a alteração.

7. Alterne para o `ConcurrencyWalkthrough` formulário em execução.

8. No primeiro registro no formulário ( `ALFKI` ), altere `ContactName` para `Maria Anders1` .

9. Selecione o botão **Salvar**.

     O erro de simultaneidade é gerado e a caixa de mensagem é exibida.

10. A seleção de **não** cancela a atualização e atualiza o conjunto de dados com os valores que estão no momento. Selecionar **Sim** grava o valor proposto no banco de dados.

## <a name="see-also"></a>Consulte Também

- [Salvar dados de volta no banco de dados](../data-tools/save-data-back-to-the-database.md)