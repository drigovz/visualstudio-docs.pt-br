---
title: Crie um arquivo de banco de dados e usar o designer de tabela
description: Tutorial que descreve como adicionar tabelas e chaves estrangeiras para um banco de dados usando o Designer de tabela no Visual Studio. Ele também mostra como adicionar dados por meio da interface gráfica.
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: afb73b316dd54284073c3d878fb35b4bb6090e08
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647239"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Criar um banco de dados e adicionar tabelas no Visual Studio

Você pode usar o Visual Studio para criar e atualizar um arquivo de banco de dados local no SQL Server Express LocalDB. Você também pode criar um banco de dados executando instruções Transact-SQL no **SQL Server Object Explorer** janela de ferramentas no Visual Studio. Neste tópico, vamos criar uma *mdf* arquivo e adicione as tabelas e chaves usando o Designer de tabela.

## <a name="prerequisites"></a>Pré-requisitos

Para concluir este passo a passo, você deve ter opcional **armazenamento de dados e processamento** carga de trabalho instalada no Visual Studio. Para instalá-lo, abra **instalador do Visual Studio** e escolha **mais** > **modificar** ao lado da versão do Visual Studio que você deseja modificar (se você tiver mais de uma versão instalada). Sobre o **cargas de trabalho** guia, em **Web e nuvem**, escolha **processamento e armazenamento de dados**e, em seguida, clique em **modificar** para adicionar a carga de trabalho Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Criar um projeto e um arquivo de banco de dados local

1. Criar um novo **aplicativo do Windows Forms** do projeto e denomine- **SampleDatabaseWalkthrough**.

2. Na barra de menus, selecione **Project** > **Adicionar Novo Item**.

3. Na lista de modelos de item, role para baixo e selecione **banco de dados baseado em serviço**.

     ![Caixa de diálogo de modelos de item](../data-tools/media/raddata-vsitemtemplates.png)

4. Nomeie o banco de dados **SampleDatabase**e, em seguida, clique em **Add**.

### <a name="add-a-data-source"></a>Adicionar uma fonte de dados

1. Se o **fontes de dados** janela não estiver aberta, abra-o pressionando **Shift**+**Alt**+**1!d** ou selecionando **Modo de exibição** > **Other Windows** > **fontes de dados** na barra de menus.

1. No **fontes de dados** janela, selecione a **Add New Data Source** link.

   O **Assistente de Configuração de Fonte de Dados** é aberto.

1. Sobre o **escolher um tipo de fonte de dados** , escolha **banco de dados** e, em seguida, escolha **próxima**.

1. Sobre o **escolha um modelo de banco de dados** , escolha **próxima** para aceitar o padrão (conjunto de dados).

1. No **escolha sua Conexão de dados** página, selecione o **SampleDatabase** file na lista suspensa e, em seguida, escolha **próxima**.

1. Sobre o **salvar a cadeia de Conexão no arquivo de configuração de aplicativo** , escolha **próxima**.

1. Um a **Choose your Database Objects** página, você verá uma mensagem informando que o banco de dados não contém todos os objetos. Escolha **Concluir**.

### <a name="view-properties-of-the-data-connection"></a>Exibir propriedades de conexão de dados

Você pode exibir a cadeia de caracteres de conexão para o *SampleDatabase* arquivo abrindo a janela de propriedades de conexão de dados:

- Selecione **modo de exibição** > **SQL Server Object Explorer** para abrir o **Pesquisador de objetos do SQL Server** janela. Expandir **(localdb) \MSSQLLocalDB** > **bancos de dados**e, em seguida, clique duas vezes em *SampleDatabase* e selecione **propriedades**.

- Como alternativa, você pode selecionar **modo de exibição** > **Gerenciador de servidores**, se essa janela não estiver aberta. Abra a janela Propriedades, expandindo a **conexões de dados** abrindo o menu de atalho do nó *SampleDatabase*e, em seguida, selecionando **propriedades**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Criar tabelas e chaves usando o Designer de tabela

Nesta seção, você criará duas tabelas, uma chave primária em cada tabela e algumas linhas de dados de exemplo. Você também criará uma chave estrangeira para especificar como os registros em uma tabela correspondem aos registros na outra tabela.

### <a name="create-the-customers-table"></a>Criar a tabela de clientes

1. Na **Gerenciador de servidores**, expanda o **conexões de dados** nó e, em seguida, expanda o **SampleDatabase** nó.

2. Abra o menu de atalho **tabelas**e, em seguida, selecione **adicionar nova tabela**.

     O **Designer de Tabela** é aberto e mostra uma grade com uma linha padrão, que representa uma única coluna na tabela que você está criando. Adicionando linhas à grade, você adicionará colunas na tabela.

3. Na grade, adicione uma linha para cada uma das seguintes entradas:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`CompanyName`|`nvarchar(50)`|Falso (desmarcado)|
    |`ContactName`|`nvarchar (50)`|Verdadeiro (marcado)|
    |`Phone`|`nvarchar (24)`|Verdadeiro (marcado)|

4. Abra o menu de atalho para o `CustomerID` de linha e, em seguida, selecione **definir chave primária**.

5. Abra o menu de atalho da linha padrão e, em seguida, selecione **excluir**.

6. Nomeie a tabela Clientes atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Você deve ver algo parecido com isso:

    ![Designer de Tabela](../data-tools/media/raddata-table-designer.png)

7. No canto superior esquerdo do **Designer de tabela**, selecione **atualização**.

8. No **atualizações de banco de dados de visualização** caixa de diálogo, selecione **Atualizar banco de dados**.

    As alterações são salvas no arquivo do banco de dados local.

### <a name="create-the-orders-table"></a>Criar a tabela Orders

1. Adicione outra tabela e uma linha para cada entrada na seguinte tabela:

    |Nome da coluna|Tipo de dados|Permitir nulos|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|Falso (desmarcado)|
    |`CustomerID`|`nchar(5)`|Falso (desmarcado)|
    |`OrderDate`|`datetime`|Verdadeiro (marcado)|
    |`OrderQuantity`|`int`|Verdadeiro (marcado)|

2. Definir **OrderID** como a chave primária e, em seguida, exclui a linha padrão.

3. Nomeie a tabela Orders atualizando a primeira linha no painel de script de acordo com o seguinte exemplo:

    ```sql
    CREATE TABLE [dbo].[Orders]
    ```

4. No canto superior esquerdo dos **Designer de tabela**, selecione o **atualização** botão.

5. No **atualizações de banco de dados de visualização** caixa de diálogo, selecione o **Atualizar banco de dados** botão.

    As alterações são salvas no arquivo do banco de dados local.

### <a name="create-a-foreign-key"></a>Criar uma chave estrangeira

1. No painel de contexto no lado direito da grade, abra o menu de atalho **chaves estrangeiras**e, em seguida, selecione **adicionar nova chave estrangeira**, como mostra a ilustração a seguir.

     ![Adicionar uma chave estrangeira no Designer de tabela](../data-tools/media/foreignkey.png)

2. Na caixa de texto exibida, substitua **ToTable** por **Clientes**.

3. No painel de T-SQL, atualize a última linha para coincidir com o exemplo a seguir:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. No canto superior esquerdo dos **Designer de tabela**, selecione o **atualização** botão.

5. No **atualizações de banco de dados de visualização** caixa de diálogo, selecione o **Atualizar banco de dados** botão.

    As alterações são salvas no arquivo do banco de dados local.

## <a name="populate-the-tables-with-data"></a>Preencher as tabelas com dados

1. Na **Gerenciador de servidores** ou **SQL Server Object Explorer**, expanda o nó para o banco de dados de exemplo.

2. Abra o menu de atalho para o **tabelas** nó, selecione **atualize**e, em seguida, expanda o **tabelas** nó.

3. Abra o menu de atalho para a tabela clientes e, em seguida, selecione **Mostrar dados da tabela**.

4. Adicione os dados que quiser para alguns clientes.

    É possível especificar cinco caracteres desejados como IDs de cliente, mas escolha pelo menos um do qual é possível se lembrar para uso posteriormente neste procedimento.

5. Abra o menu de atalho da tabela Orders e, em seguida, selecione **Mostrar dados da tabela**.

6. Adicione dados para alguns pedidos.

    > [!IMPORTANT]
    > Verifique se todas as IDs e as quantidades de pedido são inteiros e se cada ID do cliente corresponde a um valor especificado na coluna **CustomerID** da tabela Clientes.

7. Na barra de menus, selecione **arquivo** > **Salvar tudo**.

## <a name="see-also"></a>Consulte também

- [Acessando dados no Visual Studio](accessing-data-in-visual-studio.md)