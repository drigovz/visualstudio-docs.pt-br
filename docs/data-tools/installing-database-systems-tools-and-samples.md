---
title: Compatibilidade de banco de dados
ms.date: 09/06/2017
ms.topic: conceptual
helpviewer_keywords:
- database systems
- database compatibility
- databases for Visual Studio
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 94ce946f7c14706b57618f3d9aeb90cc207fcf04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648301"
---
# <a name="compatible-database-systems-for-visual-studio"></a>Sistemas de banco de dados compatíveis para Visual Studio

Para desenvolver um aplicativo conectado a dados no Visual Studio, você normalmente instala o sistema de banco de dados no computador de desenvolvimento local e, em seguida, implanta o aplicativo e o banco de dado em um ambiente de produção quando eles estão prontos. O Visual Studio instala SQL Server Express LocalDB em seu computador como parte da carga de trabalho de **armazenamento e processamento de dados** . Essa instância de LocalDB é útil para o desenvolvimento de aplicativos conectados a dados de forma rápida e fácil.

Para que um sistema de banco de dados seja acessível de aplicativos .NET e esteja visível nas janelas do Visual Studio Data Tools, ele deve ter um provedor de dados ADO.NET. Um provedor deve dar suporte especificamente A Entity Framework se você planeja usar modelos de dados de entidade em seu aplicativo .NET. Muitos provedores são oferecidos por meio do Gerenciador de pacotes NuGet ou por meio do Visual Studio Marketplace.

Se você estiver usando APIs de armazenamento do Azure, instale os emuladores de armazenamento do Azure no computador local durante o desenvolvimento para evitar cobranças até que você esteja pronto para implantar na produção. Para obter mais informações, consulte [usar o emulador de armazenamento do Azure para desenvolvimento e teste](/azure/storage/common/storage-use-emulator).

A lista a seguir inclui alguns dos sistemas de banco de dados mais populares que podem ser usados em projetos do Visual Studio. A lista não é exaustiva. Para obter uma lista de fornecedores de terceiros que oferecem provedores de dados ADO.NET que permitem uma integração profunda com ferramentas do Visual Studio, consulte [provedores de dados do ADO.net](/dotnet/framework/data/adonet/data-providers).

## <a name="microsoft-sql-server"></a>Microsoft SQL Server

SQL Server é a oferta de banco de dados principal da Microsoft. O SQL Server 2016 oferece desempenho avançado, segurança avançada e análise e relatórios avançados e integrados. Ele é fornecido em várias edições projetadas para usos diferentes: de análises de negócios altamente escalonáveis e de alto desempenho, a serem usadas em um único computador. SQL Server Express é uma edição completa do SQL Server que é adaptada para redistribuição e inserção.  O LocalDB é uma edição simplificada do SQL Server Express que não requer configuração e é executado no processo do aplicativo. Você pode baixar um ou ambos os produtos na [página de download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Muitos dos exemplos de SQL nesta seção usam SQL Server LocalDB. O SQL Server Management Studio (SSMS) é um aplicativo de gerenciamento de banco de dados autônomo que tem mais funcionalidade do que o fornecido no Visual Studio Pesquisador de Objetos do SQL Server. Você pode obter o SSMS do link anterior.

## <a name="oracle"></a>Oracle

Você pode baixar uma edição paga ou gratuita do banco de dados Oracle na página [rede de tecnologia da Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Para obter suporte ao tempo de design para Entity Framework e TableAdapters, você precisará do [Oracle Developer Tools para Visual Studio](http://www.oracle.com/technetwork/developer-tools/visual-studio/overview/index.html). Outros produtos oficiais da Oracle, incluindo o cliente Oracle Instant, estão disponíveis por meio do Gerenciador de pacotes NuGet. Você pode baixar os esquemas de exemplo do Oracle seguindo as instruções na [documentação do Oracle online](http://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

## <a name="mysql"></a>MySQL

O MySQL é um popular sistema de banco de dados de software livre que é amplamente usado em empresas e sites. Os downloads para MySQL, MySQL para Visual Studio e produtos relacionados estão no [MySQL no Windows](http://www.mysql.com/why-mysql/windows/). Terceiros oferecem várias extensões do Visual Studio e aplicativos de gerenciamento autônomos para MySQL. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas**  > **Gerenciador de pacotes NuGet**  > **gerenciar pacotes NuGet para solução**).

## <a name="postgresql"></a>PostgreSQL

O PostgreSQL é um sistema de banco de dados relacional de objeto livre e gratuito. Para instalá-lo no Windows, você pode baixá-lo na [página de download do PostgreSQL](http://www.postgresql.org/download/windows/). Você também pode criar PostgreSQL a partir do código-fonte. O sistema principal PostgreSQL inclui uma interface de linguagem C. Muitos terceiros fornecem pacotes NuGet para usar o PostgreSQL de aplicativos .NET. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas**  > **Gerenciador de pacotes NuGet**  > **gerenciar pacotes NuGet para solução**). Talvez, o pacote mais popular seja fornecido pelo [npgsql.org](http://www.npgsql.org).

## <a name="sqlite"></a>SQLite

O SQLite é um mecanismo de banco de dados SQL inserido que é executado no próprio processo do aplicativo. Você pode baixá-lo na [página de download do SQLite](http://www.sqlite.org/download.html). Muitos pacotes NuGet de terceiros para SQLite também estão disponíveis. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas**  > **Gerenciador de pacotes NuGet**  > **gerenciar pacotes NuGet para solução**).

## <a name="firebird"></a>Firebird

Firebird é um sistema de banco de dados SQL de código aberto. Você pode baixá-lo na [página de download do Firebird](http://firebirdsql.org/en/downloads/). Um provedor de dados ADO.NET está disponível por meio do Gerenciador de pacotes NuGet.

## <a name="see-also"></a>Consulte também

- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Como determinar a versão e a edição do SQL Server e seus componentes](http://support.microsoft.com/kb/321185)