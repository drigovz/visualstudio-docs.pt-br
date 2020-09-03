---
title: Criar um banco de dados SQL usando um script | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670085"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Criar um banco de dados SQL usando um script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste tutorial, você usará o Visual Studio para criar um banco de dados pequeno que contenha o código de exemplo para [criar um aplicativo simples, usando ADO.net](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **Neste tópico**

- [Criar um script que contenha um esquema de banco de dados](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Criar um projeto de banco de dados e importar um esquema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Implantar o banco de dados](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Pré-requisitos
 Para concluir este passo a passos, você deve ter SQL Server Express LocalDB ou outro banco de dados SQL instalado.

## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a> Criar um script que contenha um esquema de banco de dados

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Para criar um script a partir do qual você possa importar um esquema

1. No [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , na barra de menus, selecione **arquivo**  >  **novo**  >  **arquivo**.

     A caixa de diálogo **Novo Arquivo** será exibida.

2. Na lista **categorias** , selecione **geral**.

3. Na lista **modelos** , selecione **arquivo SQL**e, em seguida, selecione o botão **abrir** .

     O Editor Transact-SQL é aberto.

4. Copie o código Transact-SQL a seguir e cole-o no Editor Transact-SQL.

    ```
    PRINT N'Creating Sales...';
    GO
    CREATE SCHEMA [Sales]
        AUTHORIZATION [dbo];
    GO
    PRINT N'Creating Sales.Customer...';
    GO
    CREATE TABLE [Sales].[Customer] (
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,
        [CustomerName] NVARCHAR (40) NOT NULL,
        [YTDOrders]    INT           NOT NULL,
        [YTDSales]     INT           NOT NULL
    );
    GO
    PRINT N'Creating Sales.Orders...';
    GO
    CREATE TABLE [Sales].[Orders] (
        [CustomerID] INT      NOT NULL,
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,
        [OrderDate]  DATETIME NOT NULL,
        [FilledDate] DATETIME NULL,
        [Status]     CHAR (1) NOT NULL,
        [Amount]     INT      NOT NULL
    );
    GO
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];
    GO
    PRINT N'Creating Sales.Def_Customer_YTDSales...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];
    GO
    PRINT N'Creating Sales.Def_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];
    GO
    PRINT N'Creating Sales.Def_Orders_Status...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];
    GO
    PRINT N'Creating Sales.PK_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Customer]
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.PK_Orders_OrderID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);
    GO
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;
    GO
    PRINT N'Creating Sales.CK_Orders_FilledDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.CK_Orders_OrderDate...';
    GO
    ALTER TABLE [Sales].[Orders]
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));
    GO
    PRINT N'Creating Sales.uspCancelOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspCancelOrder]
    @OrderID INT
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'X'
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders - @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspFillOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspFillOrder]
    @OrderID INT, @FilledDate DATETIME
    AS
    BEGIN
    DECLARE @Delta INT, @CustomerID INT
    BEGIN TRANSACTION
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Orders]
       SET [Status] = 'F',
           [FilledDate] = @FilledDate
    WHERE [OrderID] = @OrderID;

    UPDATE [Sales].[Customer]
       SET
       YTDSales = YTDSales + @Delta
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    END
    GO
    PRINT N'Creating Sales.uspNewCustomer...';
    GO
    CREATE PROCEDURE [Sales].[uspNewCustomer]
    @CustomerName NVARCHAR (40),
    @CustomerID INT OUTPUT
    AS
    BEGIN
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);
    SET @CustomerID = SCOPE_IDENTITY();
    RETURN @@ERROR
    END
    GO
    PRINT N'Creating Sales.uspPlaceNewOrder...';
    GO
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'
    AS
    BEGIN
    DECLARE @RC INT
    BEGIN TRANSACTION
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)
    SELECT @RC = SCOPE_IDENTITY();
    UPDATE [Sales].[Customer]
       SET
       YTDOrders = YTDOrders + @Amount
        WHERE [CustomerID] = @CustomerID
    COMMIT TRANSACTION
    RETURN @RC
    END
    GO
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]
    @CustomerID INT=0
    AS
    BEGIN
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]
      FROM [Sales].[Customer] AS C
      INNER JOIN [Sales].[Orders] AS O
         ON [O].[CustomerID] = [C].[CustomerID]
      WHERE [C].[CustomerID] = @CustomerID
    END
    GO
    ```

5. Na barra de menus, selecione **arquivo**  >  **salvar SqlQuery_1. SQL como**.

     A caixa de diálogo **salvar arquivo como** é exibida.

6. Na caixa **nome do arquivo** , digite `SampleImportScript.sql` , observe o local onde você salvará o arquivo e, em seguida, selecione o botão **salvar** .

7. Na barra de menus, selecione **arquivo**  >  **fechar solução**.

     Em seguida, crie um projeto de banco de dados e importe o esquema do script que você criou.

## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProject"></a> Criar um projeto de banco de dados e importar um esquema

#### <a name="to-create-a-database-project"></a>Para criar um projeto de banco de dados

1. Na barra de menus, selecione **arquivo**  >  **novo**  >  **projeto**.

     A caixa de diálogo **Novo Projeto** aparecerá.

2. Em **instalado**, expanda o nó **modelos** , expanda o nó **outros idiomas** , selecione a categoria **SQL Server** e, em seguida, selecione o modelo de projeto de **banco de dados SQL Server** .

    > [!NOTE]
    > O nó **outros idiomas** não aparece em todas as instalações do Visual Studio.

3. Na caixa **nome** , digite `Small Database` .

4. Marque a caixa de seleção **criar diretório para solução** se ela ainda não estiver selecionada.

5. Desmarque a caixa de seleção **Adicionar ao controle do código-fonte** se ela ainda não estiver desmarcada e, em seguida, selecione o botão **OK** .

     O projeto de banco de dados é criado e aparece no **Gerenciador de Soluções**.

     Em seguida, importe o esquema de banco de dados do script.

#### <a name="to-import-a-database-schema-from-a-script"></a>Para importar um esquema de banco de dados de um script.

1. Na barra de menus, selecione **projeto**  >  **importar**  >  **script**.

2. Na página de **boas-vindas** , examine o texto e, em seguida, selecione o botão **Avançar** .

3. Selecione o botão de opção **arquivo único** e, em seguida, selecione o botão **procurar** .

     A caixa de diálogo **Importar Script SQL** é exibida.

4. Abra a pasta em que você salvou o arquivo SampleImportScript. SQL, selecione o arquivo e, em seguida, selecione o botão **abrir** .

5. Selecione o botão **concluir** para fechar a caixa de diálogo **Importar Script SQL** .

     O script é importado e os objetos que o script define são adicionados ao seu projeto de banco de dados.

6. Examine o resumo e clique no botão **concluir** para fechar a caixa de diálogo **Importar arquivo de script SQL** .

7. Em **Gerenciador de soluções**, expanda as pastas vendas, scripts e segurança do seu projeto e verifique se elas contêm arquivos. Sql.

8. Em **pesquisador de objetos do SQL Server**, verifique se o banco de dados aparece no nó **projetos** .

     Neste ponto, o banco de dados contém apenas objetos do sistema, como tabelas e procedimentos armazenados. Depois de implantar o banco de dados, ele conterá as tabelas de usuário e os procedimentos armazenados que os scripts definem.

## <a name="deploy-the-database"></a><a name="DeployDatabase"></a> Implantar o banco de dados
 Quando você pressiona a tecla **F5** , implanta (ou publica) o banco de dados em um banco de dados LocalDB por padrão. Você pode implantar o banco de dados em um local diferente abrindo a página de propriedades do projeto, selecionando a guia **depurar** e, em seguida, alterando a cadeia de conexão.
