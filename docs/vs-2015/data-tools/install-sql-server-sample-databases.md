---
title: Instalar SQL Server bancos de dados de exemplo | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3991d3b741162b4b1993e5359ad427c17f00321a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651524"
---
# <a name="install-sql-server-sample-databases"></a>Instalar bancos de dados de exemplo do SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os bancos de dados de exemplo são úteis para experimentar consultas do SQL e do LINQ, DataBinding, Entity Framework modelagem e assim por diante.  Cada produto de banco de dados tem seus próprios bancos de dados de exemplo. A Northwind e a AdventureWorks são dois bancos de dados de exemplo populares SQL Server.

 O **AdventureWorks** é o banco de dados de exemplo atual fornecido para produtos SQL Server. Você pode baixá-lo como um arquivo. MDF da [página AdventureWorks no CodePlex](http://msftdbprodsamples.codeplex.com/). Há versões normais e leves (LT) do banco de dados disponíveis aqui. Na maioria dos cenários, a versão de LT é preferida porque é menos complexa.

 A **Northwind** é um banco de dados SQL Server relativamente simples que foi usado há muitos anos. Você pode baixá-lo como um arquivo. bak da [página do banco de dados Northwind no CodePlex](https://northwinddatabase.codeplex.com/). Para evitar problemas de permissões, descompacte o arquivo em uma nova pasta que não esteja sob sua pasta de usuário.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Para restaurar um banco de dados de um arquivo. bak no Visual Studio

1. Quando você faz backup de um banco de dados Microsoft SQL Server, o resultado é um arquivo. bak. Para tornar o arquivo. bak utilizável novamente como um arquivo de banco de dados, ele deve ser *restaurado*. No menu principal, selecione **exibir**  > **pesquisador de objetos do SQL Server**. Se você não o vir, talvez seja necessário instalá-lo. Vá para o **painel de controle**  > **programas e recursos**, localize Microsoft Visual Studio 2015 e clique no botão **alterar** . Quando a lista de componentes instalados aparecer na janela do instalador, marque a caixa de seleção **pesquisador de objetos do SQL Server** e continue com a instalação.

2. Em Pesquisador de Objetos do SQL Server, clique com o botão direito do mouse em qualquer mecanismo de banco de dados SQL Server (por exemplo, LocalDB) e selecione**nova consulta**.

     ![Pesquisador de Objetos do SQL Server nova consulta](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Pesquisador de Objetos do SQL Server nova consulta")

3. Primeiro, você precisa dos nomes lógicos do banco de dados e dos arquivos de log dentro do arquivo. bak. Para obtê-lo, insira essa consulta no editor de consultas SQL e, em seguida, selecione o botão verde **executar** na parte superior da janela. Modifique o caminho do arquivo, se necessário, para apontar para o arquivo. bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Anote os nomes lógicos que aparecem na janela resultados.  Para o banco de dados Northwind, os dois nomes lógicos são Northwind e Northwind_log.

4. Agora, execute esta consulta para criar o banco de dados. Substitua seus próprios caminhos de origem e de destino, nomes de bancos de dados lógicos e nomes de arquivos físicos para Northwind, conforme apropriado. Mantenha as extensões de arquivo. MDF e. ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. No Pesquisador de Objetos do SQL Server, clique com o botão direito do mouse no nó **bancos** de dados e você deverá ver o nó do Northwind Database. Caso contrário, clique com o botão direito do mouse em bancos de **dados e selecione Adicionar novo Database**. Insira o nome e o local do arquivo. MDF que você acabou de criar.

6. Agora, o banco de dados está pronto para ser usado como uma fonte de dado no Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Para restaurar um banco de dados de um arquivo. bak no SQL Server Management Studio

1. Baixe SQL Server Management Studio do site de download.

2. Na janela do **pesquisador de objetos** do SSMS, clique com o botão direito do mouse no nó **bancos** de dados, selecione**Restaurar Banco**e forneça o local do arquivo. bak.

     ![Banco de dados de restauração do SSMS](../data-tools/media/raddata-ssms-restore-database.png "Banco de dados de restauração do raddata SSMS")
