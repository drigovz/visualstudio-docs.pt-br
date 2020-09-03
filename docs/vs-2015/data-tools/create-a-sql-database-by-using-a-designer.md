---
title: Criar um banco de dados SQL usando um designer | Microsoft Docs
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
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651056"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Criar um banco de dados SQL usando um designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode explorar tarefas básicas, como adicionar tabelas e definir colunas, usando o Visual Studio para criar e atualizar um arquivo de banco de dados local no SQL Server Express LocalDB. Depois de concluir essa explicação passo a passo, você poderá descobrir recursos mais avançados usando o banco de dados local como um ponto de partida para outras explicações passo a passo que o exigem.

 Você também pode criar um banco de dados usando as instruções SQL Server Management Studio (um download separado) ou Transact-SQL na janela de ferramentas do **pesquisador de objetos do SQL Server** no Visual Studio.

 Durante essa explicação passo a passo, você explorará as seguintes tarefas:

- [Criar um projeto e um arquivo de banco de dados local](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Criar tabelas, colunas, chaves primárias e chaves estrangeiras](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Preencher as tabelas com dados](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passos, verifique se você tem SQL Server Data Tools instalado. No menu **Exibir** , você deve ver **pesquisador de objetos do SQL Server**. Se não estiver lá, vá para **Adicionar ou remover programas**, clique em **Visual Studio 2015**, selecione **alterar**e selecione a caixa ao lado de **SQL Server Data Tools**.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> Criar um projeto e um arquivo de banco de dados local

#### <a name="to-create-a-project-and-a-database-file"></a>Para criar um projeto e um arquivo de banco de dados

1. Crie um projeto Windows Forms que é nomeado `SampleDatabaseWalkthrough` .

2. Na barra de menus, selecione **projeto**  >  **Adicionar novo item**.

3. Na lista de modelos de item, role para baixo e selecione **banco de dados baseado em serviço**.

    ![Caixa de diálogo modelos de item](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Nomeie o banco de dados **SampleDatabase**e, em seguida, selecione o botão **Adicionar** .

5. Se a janela **fontes de dados** não estiver aberta, abra-a selecionando as teclas Shift + Alt + D ou, na barra de menus, selecionando **Exibir**  >  **outras**  >  **fontes de dados**do Windows.

6. Na janela **fontes de dados** , selecione o link **Adicionar nova fonte de dados** .

7. No **Assistente de configuração da fonte de dados**, selecione o botão **Avançar** quatro vezes para aceitar as configurações padrão e, em seguida, selecione o botão **concluir** .

   Abrindo-se a janela de propriedades do banco de dados, é possível exibir sua cadeia de conexão e o local do arquivo .mdf principal. Você verá que o arquivo de banco de dados está na pasta do projeto.

- No Visual Studio, selecione **Exibir**  >  **pesquisador de objetos do SQL Server** se essa janela ainda não estiver aberta. Abra a janela Propriedades expandindo o nó **conexões de dados** , abrindo o menu de atalho para SampleDatabase. MDF e, em seguida, selecionando **Propriedades**.

- Como alternativa, você pode selecionar **Exibir**  >  **Gerenciador de servidores**, se essa janela ainda não estiver aberta. Abra a janela Propriedades expandindo o nó **conexões de dados** . Abra o menu de atalho para SampleDatabase. MDF e selecione **Propriedades**.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> Criar tabelas, colunas, chaves primárias e chaves estrangeiras
 Nesta seção, você criará algumas tabelas, uma chave primária em cada tabela e algumas linhas de dados de exemplo. Na próxima explicação passo a passo, você terá uma idea de como essas informações podem ser exibidas em um aplicativo. Você também criará uma chave estrangeira para especificar como os registros em uma tabela podem corresponder aos registros na outra tabela.

#### <a name="to-create-the-customers-table"></a>Para criar a tabela Customers

1. Em **Gerenciador de servidores** ou **pesquisador de objetos do SQL Server**, expanda o nó **conexões de dados** e, em seguida, expanda o nó **SampleDatabase. MDF** .

2. Abra o menu de atalho para **tabelas**e, em seguida, selecione **Adicionar nova tabela**.

     O **Designer de Tabela** é aberto e mostra uma grade com uma linha padrão, que representa uma única coluna na tabela que você está criando. Adicionando linhas à grade, você adicionará colunas na tabela.

3. Na grade, adicione uma linha para cada uma das seguintes entradas:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`CompanyName`|`nvarchar(50)`|Falso (desmarcado)|
    |`ContactName`|`nvarchar (50)`|Verdadeiro (marcado)|
    |`Phone`|`nvarchar (24)`|Verdadeiro (marcado)|

4. Abra o menu de atalho da `CustomerID` linha e, em seguida, selecione **definir chave primária**.

5. Abra o menu de atalho para a linha padrão e, em seguida, selecione **excluir**.

6. Nomeie a tabela Clientes atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     Você deverá ver algo como:

     ![Criador de Tabelas](../data-tools/media/raddata-table-designer.png "Designer de Tabela raddata")

7. No canto superior esquerdo da **Designer de tabela**, selecione o botão **Atualizar** .

8. Na caixa de diálogo **Visualizar atualizações do banco de dados** , selecione o botão **Atualizar banco de dados** .

     As alterações são salvas no arquivo do banco de dados local.

#### <a name="to-create-the-orders-table"></a>Para criar a tabela Orders

1. Adicione outra tabela e uma linha para cada entrada na seguinte tabela:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|Falso (desmarcado)|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`OrderDate`|`datetime`|Verdadeiro (marcado)|
    |`OrderQuantity`|`int`|Verdadeiro (marcado)|

2. Defina **OrderID** como a chave primária e, em seguida, exclua a linha padrão.

3. Nomeie a tabela Orders atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. No canto superior esquerdo da **Designer de tabela**, selecione o botão **Atualizar** .

5. Na caixa de diálogo **Visualizar atualizações do banco de dados** , selecione o botão **Atualizar banco de dados** .

     As alterações são salvas no arquivo do banco de dados local.

#### <a name="to-create-a-foreign-key"></a>Para criar uma chave estrangeira

1. No painel de contexto no lado direito da grade, abra o menu de atalho para **chaves estrangeiras**e, em seguida, selecione **Adicionar nova chave estrangeira**, como mostra a ilustração a seguir.

     ![Adicionando uma chave estrangeira no Designer de Tabela](../data-tools/media/foreignkey.png "ForeignKey")

2. Na caixa de texto exibida **, substitua por** `Customers` .

3. No painel T-SQL, atualize a última linha para corresponder ao exemplo a seguir:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. No canto superior esquerdo da **Designer de tabela**, selecione o botão **Atualizar** .

5. Na caixa de diálogo **Visualizar atualizações do banco de dados** , selecione o botão **Atualizar banco de dados** .

     As alterações são salvas no arquivo do banco de dados local.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> Preencher as tabelas com dados

#### <a name="to-populate-the-tables-with-data"></a>Para popular as tabelas com dados

1. Em **Gerenciador de servidores** ou **pesquisador de objetos do SQL Server**, expanda o nó do banco de dados de exemplo.

2. Abra o menu de atalho para o nó **tabelas** , selecione **Atualizar**e, em seguida, expanda o nó **tabelas** .

3. Abra o menu de atalho da tabela clientes e selecione **Mostrar dados da tabela**.

4. Adicione os dados desejados para pelo menos três clientes.

     É possível especificar cinco caracteres desejados como IDs de cliente, mas escolha pelo menos um do qual é possível se lembrar para uso posteriormente neste procedimento.

5. Abra o menu de atalho da tabela pedidos e selecione **Mostrar dados da tabela**.

6. Adicione dados para pelo menos três pedidos.

    > [!IMPORTANT]
    > Verifique se todas as IDs e as quantidades de pedido são inteiros e se cada ID do cliente corresponde a um valor especificado na coluna CustomerID da tabela Customers.

7. Na barra de menus, selecione **arquivo**  >  **salvar tudo**.

8. Na barra de menus, selecione **arquivo**  >  **fechar solução**.

    > [!NOTE]
    > Como prática recomendada, é possível fazer backup do arquivo de banco de dados recém-criado copiando-o e colando a cópia em outro local ou dando à cópia um nome diferente.

## <a name="next-steps"></a>Próximas etapas
 Agora que você tem um arquivo de banco de dados local com algum dado de exemplo, você pode concluir qualquer um dos passo a passos que demonstram tarefas de banco.
