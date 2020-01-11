---
title: Accessing data
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 065a6ae3901f2426db6556cb19e80f543cb8a78f
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846663"
---
# <a name="accessing-data-in-visual-studio"></a>Acessando dados no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio, you can create applications that connect to data in virtually any database product or service, in any format, anywhere—on a local machine, on a local area network, or in a public, private, or hybrid cloud.

 For applications in JavaScript, Python, PHP, Ruby, or C++, you connect to data like you do anything else, by obtaining libraries and writing code. For .NET applications, Visual Studio provides tools that you can use to explore data sources,  create object models to store and manipulate data in memory, and bind data to the user interface.     Microsoft Azure provides SDKs for .NET, Java, Node.js, PHP, Python, Ruby, and mobile apps, and tools in Visual Studio for connecting to Azure Storage.

 The following lists show just a few of the many database and storage systems that can be used from Visual Studio. The [Microsoft Azure](https://azure.microsoft.com/) offerings are data services that include all provisioning and administration of the  underlying data store.  [Azure Tools for Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) is an optional component that enables you to work with Azure data stores directly from Visual Studio. Most of the other SQL and NoSQL database products that are listed here can be hosted on a local machine, on a local network, or in Microsoft Azure on a virtual machine. In this scenario, you are responsible for managing the database itself.

 **Microsoft Azure**

||||
|-|-|-|
|Banco de dados SQL|DocumentDB|Storage (blobs, tables, queues, files)|
|SQL Data Warehouse|SQL Server Stretch Database|StorSimple|

 E muito mais...

 **SQL**

||||
|-|-|-|
|SQL Server 2005–2016, including Express and LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|SQLite|||

 E muito mais...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|NDatabase|OrientDB|RavenDB|
|VelocityDB|||

 E muito mais...

 Many database vendors and third parties support Visual Studio integration by NuGet packages. You can explore the offerings on nuget.org or through the NuGet Package Manager in Visual Studio (**Tools** > **NuGet Package Manager** > **Manage NuGet Packages for Solution**). Other database products integrate with Visual Studio as an extension.   You can browse these offerings in the Visual Studio Gallery by navigating to **Tools** > **Extensions and Updates** and then selecting **Online** in the left pane of the dialog box.  For more information, see [Installing database systems, tools, and samples](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> O suporte estendido para o SQL Server 2005 terminou em 12 de abril de 2016.   There is no guarantee that data tools in Visual Studio 2015 and later will continue to work with SQL Server 2005 after this date. For more information, see the [end-of-support announcement for SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Linguagens .NET
 All .NET data access, including in .NET Core,  is based on ADO.NET, a set of classes that defines an interface for accessing any kind of data source, both relational and non-relational. Visual Studio has several tools and designers that work with ADO.NET to help you connect to databases, manipulate the data, and present the data to the user. The documentation in this section describes how to use those tools. You can also program directly against the ADO.NET command objects. For more information about calling the ADO.NET APIs directly, see [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) in the MSDN Library.

 For data-access documentation specifically related to ASP.NET, see  [Working with Data](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) on the ASP.NET site. For a tutorial on using Entity Framework with ASP.NET MVC, see [Getting Started with Entity Framework 6 Code First using MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Universal Windows Platform (UWP) apps in C# or Visual Basic can use the      Microsoft Azure SDK for .NET to access Azure Storage and other Azure services. The Windows.Web.HttpClient class enables communication with any RESTful service. For more information, see [How to connect to an HTTP server using Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 For data storage on the local machine, the recommended approach is to use SQLite, which runs in the same process as the app. If an object-relational mapping (ORM) layer is required, you can use Entity Framework. For more information, see [Data access](https://msdn.microsoft.com/windows/uwp/data-access/index) in the Windows Developer Center.

 If you are connecting to Azure services, be sure to download the latest [Azure SDK tools](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Provedores de dados
 For a database to be consumable in ADO.NET, it must have a custom *ADO.NET data provider* or else must expose an ODBC or OLE DB interface. Microsoft provides a [list of ADO.NET data providers](https://msdn.microsoft.com/data/dd363565) for SQL Server products as well as ODBC and OLE DB providers.

#### <a name="data-modeling"></a>Modelagem de dados
 In .NET, you have three choices for modeling and manipulating data in memory after you have retrieved it from a data source:

 Entity Framework The preferred Microsoft ORM technology. You can use it to program against relational data as first-class .NET objects. Para novos aplicativos, deve ser a primeira opção padrão quando um modelo é necessário. Ele requer suporte personalizado do provedor de ADO.NET subjacente.

 LINQ to SQL um mapeador relacional de objeto de geração anterior. Ele funciona bem para cenários menos complexos, mas não está mais no desenvolvimento ativo.

 DataSets é o mais antigo das três tecnologias de modelagem. Ele foi projetado principalmente para o desenvolvimento rápido de aplicativos de "formulários em dados" nos quais você não está processando grandes quantidades de dados ou realizando consultas ou transformações complexas. Um objeto DataSet consiste em objetos DataTable e DataRow que se assemelham logicamente a objetos do banco de dados SQL muito mais do que objetos .NET. Para aplicativos relativamente simples com base em fontes de dados SQL, os DataSets ainda podem ser uma boa opção.

 Não há nenhum requisito para usar nenhuma dessas tecnologias. Em alguns cenários, especialmente onde o desempenho é crítico, você pode simplesmente usar um objeto DataReader para ler do banco de dados e copiar os valores necessários para um objeto de coleção, como List\<T >.

### <a name="native-c"></a>C++ Nativo
 C++os aplicativos que se conectam ao SQL Server devem usar o [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Você pode acessar outros bancos de dados usando os drivers [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) ou OLE DB diretamente. O ODBC é a interface de banco de dados padrão atual, mas a maioria dos sistemas de banco de dados fornece uma funcionalidade personalizada que não pode ser acessada pela interface ODBC.  OLE DB é uma tecnologia de acesso a dados COM herdada que ainda é suportada, mas não é recomendada para novos aplicativos.  Para obter mais informações, consulte [acesso a dados](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++programas que consomem serviços REST podem usar o [ C++ SDK REST](https://github.com/Microsoft/cpprestsdk).

 C++programas que funcionam com Armazenamento do Microsoft Azure podem usar o [cliente armazenamento do Microsoft Azure](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelagem de dados
 O Visual Studio não fornece uma camada de ORM C++para.  [ODB](https://www.codesynthesis.com/products/odb/) é um popular ORM de código-fonte C++aberto para o.

 Para obter mais informações sobre as C++ tecnologias de acesso a dados visuais herdadas, consulte [acesso a dados](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 O [JavaScript no Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) é uma linguagem de primeira classe para a criação de aplicativos de plataforma cruzada, aplicativos UWP, serviços de nuvem, sites e aplicativos Web. Você pode usar Bower, grunt, Gulp, NPM e NuGet de dentro do Visual Studio para instalar suas bibliotecas JavaScript favoritas e seus produtos de banco de dados. Conecte-se ao armazenamento do Azure e aos serviços baixando SDKs do [site do Azure](https://azure.microsoft.com/).  O Edge. js é uma biblioteca que conecta o JavaScript do lado do servidor (Node. js) a fontes de dados do ADO.NET.

### <a name="python"></a>Python
 Instale [ferramentas Python para Visual Studio](http://microsoft.github.io/PTVS/) junto com sua estrutura de Python favorita para criar aplicativos CPython ou IronPython (.net).  O site Ferramentas Python para Visual Studio tem vários tutoriais sobre como se conectar a dados, incluindo [Django e banco de dados SQL no Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django e MySQL no Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) e [garrafa e MongoDB no Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>Nesta seção
 [Instalando sistemas de banco de dados, ferramentas e exemplos](../data-tools/installing-database-systems-tools-and-samples.md) Discute como obter produtos de banco de dados e as extensões ou os drivers do Visual Studio que dão suporte a eles e onde encontrar bancos de dados de exemplo para fins de experimentação e aprendizado.

 [Ferramentas de dados do Visual Studio para .net](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Descreve como usar as janelas de ferramentas do Visual Studio para se conectar a fontes de dados, criar conjuntos ou Entity Framework modelos e associar os dados aos controles da interface do usuário.

## <a name="related-topics"></a>Tópicos relacionados
 [Dados, dispositivos e análises](https://msdn.microsoft.com/data-and-devices) Fornece uma introdução à nuvem inteligente da Microsoft, incluindo o Cortana Analytics Suite e suporte para Internet das Coisas.

 [Armazenamento do Microsoft Azure](/azure/storage/) Descreve o armazenamento do Azure e como criar aplicativos usando BLOBs, tabelas, filas e arquivos do Azure.

 [Banco de dados SQL do Azure](https://azure.microsoft.com/documentation/services/sql-database/) Descreve como se conectar ao banco de dados SQL do Azure, um banco de dados relacional como um serviço.

 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Descreve as ferramentas que simplificam o design, a exploração, o teste e a implantação de aplicativos e bancos de dados conectados a data.

 [ADO.net](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) Descreve a arquitetura ADO.NET e como usar as classes ADO.NET para gerenciar dados de aplicativos e interagir com fontes de dados e XML.

 [Entity Framework ADO.net](https://msdn.microsoft.com/data/ef) Descreve como criar aplicativos de dados que permitem aos desenvolvedores programar em um modelo conceitual em vez de diretamente em relação a um banco de dados relacional.

 [WCF Data Services 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Descreve como usar [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] para implantar serviços de dados na Web ou em uma intranet que implementam o [protocolo Open Data (OData)](https://www.odata.org/).

 [Dados em soluções do Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Contém links para tópicos que explicam como os dados funcionam em soluções do Office. Isso inclui informações sobre programação orientada a esquema, cache de dados e acesso a dados no servidor.

 [LINQ (consulta integrada à linguagem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Descreve os recursos de consulta incorporados ao C# e Visual Basic e o modelo comum para consultar bancos de dados relacionais, documentos XML, DataSets e coleções na memória.

 [Ferramentas XML no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) Discute o trabalho com dados XML, a depuração de XSLT, .NET Framework recursos XML e a arquitetura da consulta XML.

 [Documentos e dados XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Fornece uma visão geral de um conjunto abrangente e integrado de classes que funcionam com documentos e dados XML no .NET Framework.
