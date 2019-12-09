---
title: Instalando sistemas de banco de dados, ferramentas e exemplos | Microsoft Docs
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
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299599"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalando sistemas, ferramentas e exemplos de banco de dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio em si não inclui nenhum sistema de banco de dados que não seja usado internamente. Para desenvolver um aplicativo conectado a dados no Visual Studio, você normalmente instala o sistema de banco de dados no computador de desenvolvimento local e, em seguida, implanta o aplicativo e o banco de dado em um ambiente de produção quando eles estão prontos. Para que o sistema de banco de dados seja acessível de aplicativos .NET e esteja visível nas janelas do Visual Studio Data Tools, ele deve ter um provedor de dados ADO.NET. Um provedor deve dar suporte especificamente A Entity Framework se você planeja usar modelos de dados de entidade em seu aplicativo .NET.     Muitos provedores são oferecidos por meio do Gerenciador de pacotes NuGet ou por meio da galeria do Visual Studio.

 Para o desenvolvimento do SQL, verifique se você tem SQL Server Data Tools instalado no Visual Studio. Clique no menu **Exibir** . Se você não vir Pesquisador de Objetos do SQL Server, vá para o painel de controle e altere o Visual Studio. No instalador, selecione **Microsoft SQL Server Data Tools**.

 Se você estiver usando APIs de armazenamento do Azure, instale os emuladores de armazenamento do Azure no computador local durante o desenvolvimento para evitar cobranças até que você esteja pronto para implantar na produção. Para obter mais informações, consulte [usar o emulador de armazenamento do Azure para desenvolvimento e teste](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 A lista a seguir inclui alguns dos sistemas de banco de dados mais populares que podem ser usados em projetos do Visual Studio. A lista não é exaustiva. Para obter uma lista de fornecedores de terceiros que oferecem provedores de dados ADO.NET que permitem uma integração profunda com ferramentas do Visual Studio, consulte [provedores de dados do ADO.net](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server é a oferta de banco de dados principal da Microsoft. O SQL Server 2016 oferece desempenho avançado, segurança avançada e análise e relatórios avançados e integrados. Ele é fornecido em várias edições projetadas para usos diferentes: de análises de negócios altamente escalonáveis e de alto desempenho, a serem usadas em um único computador. SQL Server Express é uma edição completa do SQL Server que é adaptada para redistribuição e inserção.  O LocalDB é uma edição simplificada do SQL Server Express que não requer configuração e é executado no processo do aplicativo. Você pode baixar um ou ambos os produtos na [página de download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Muitos dos exemplos de SQL nesta seção usam SQL Server LocalDB. O SQL Server Management Studio (SSMS) é um aplicativo de gerenciamento de banco de dados autônomo que tem mais funcionalidade do que o fornecido no Visual Studio Pesquisador de Objetos do SQL Server. Você pode obter o SSMS do link anterior.

### <a name="oracle"></a>Oracle
 Você pode baixar uma edição paga ou gratuita do banco de dados Oracle na página [rede de tecnologia da Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) . Para obter suporte de tempo de design para Entity Framework e TableAdapters, você precisará do [ferramentas para desenvolvedores Oracle para Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Outros produtos oficiais da Oracle, incluindo o cliente Oracle Instant, estão disponíveis por meio do Gerenciador de pacotes NuGet.  Você pode baixar os esquemas de exemplo do Oracle seguindo as instruções na [documentação do Oracle online](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 O MySQL é um popular sistema de banco de dados de software livre que é amplamente usado em empresas e sites. Os downloads para MySQL, MySQL para Visual Studio e produtos relacionados estão no [MySQL no Windows](https://www.mysql.com/why-mysql/windows/).  Terceiros oferecem várias extensões do Visual Studio e aplicativos de gerenciamento autônomos para MySQL. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas** > **Gerenciador de pacotes NuGet** > **gerenciar pacotes NuGet para solução**).

### <a name="postgresql"></a>PostgreSQL
 O PostgreSQL é um sistema de banco de dados relacional de objeto livre e gratuito. Para instalá-lo no Windows, você pode baixá-lo na [página de download do PostgreSQL](http://www.postgresql.org/download/windows/).  Você também pode criar PostgreSQL a partir do código-fonte.  O sistema principal PostgreSQL inclui uma interface de linguagem C. Muitos terceiros fornecem pacotes NuGet para usar o PostgreSQL de aplicativos .NET.  Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas** > **Gerenciador de pacotes NuGet** > **gerenciar pacotes NuGet para solução**). Talvez o pacote mais popular seja fornecido pelo [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>SQLite
 O SQLite é um mecanismo de banco de dados SQL inserido que é executado no próprio processo do aplicativo. Você pode baixá-lo na [página de download do SQLite](http://www.sqlite.org/download.html). Muitos pacotes NuGet de terceiros para SQLite também estão disponíveis. Você pode procurar as ofertas no Gerenciador de pacotes do NuGet (**ferramentas** > **Gerenciador de pacotes NuGet** > **gerenciar pacotes NuGet para solução**).

### <a name="firebird"></a>Firebird
 Firebird é um sistema de banco de dados SQL de código aberto. Você pode baixá-lo na [página de download do Firebird](http://firebirdsql.org/en/downloads/). Um provedor de dados ADO.NET está disponível por meio do Gerenciador de pacotes NuGet.

## <a name="see-also"></a>Consulte também
 [Como determinar a versão e a edição do SQL Server e seus componentes](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
