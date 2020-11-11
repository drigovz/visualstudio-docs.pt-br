---
title: Trabalhar com dados no Visual Studio
description: Trabalhar com dados no Visual Studio. Crie aplicativos que se conectam a dados em outros produtos ou serviços de banco de dados em máquinas locais, LANs ou nuvens públicas ou privadas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: a5458ffca549026c99c8faedc8f47d3f3285a7ca
ms.sourcegitcommit: 63ff7cb85b3baeeb713240d17bb2a18497f3741d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94518733"
---
# <a name="work-with-data-in-visual-studio"></a>Trabalhar com dados no Visual Studio

No Visual Studio, você pode criar aplicativos que se conectam a dados em praticamente qualquer produto ou serviço de banco de dado, em qualquer formato, em qualquer lugar — em um computador local, em uma rede local ou em uma nuvem pública, privada ou híbrida.

Para aplicativos em JavaScript, Python, PHP, Ruby ou C++, você se conecta a dados como faz qualquer outra coisa, obtendo bibliotecas e escrevendo código. Para aplicativos .NET, o Visual Studio fornece ferramentas que você pode usar para explorar fontes de dados, criar modelos de objeto para armazenar e manipular dados na memória e associar dados à interface do usuário. O Microsoft Azure fornece SDKs para .NET, Java, Node.js, PHP, Python, Ruby e aplicativos móveis e ferramentas no Visual Studio para se conectar ao armazenamento do Azure.

::: moniker range="vs-2017"
As listas a seguir mostram apenas alguns dos vários sistemas de banco de dados e de armazenamento que podem ser usados no Visual Studio. As ofertas de [Microsoft Azure](https://azure.microsoft.com/) são serviços de dados que incluem todo o provisionamento e a administração do armazenamento de dados subjacente. A carga de trabalho de **desenvolvimento do Azure** no [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) permite que você trabalhe com armazenamentos de dados do Azure diretamente do Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
As listas a seguir mostram apenas alguns dos vários sistemas de banco de dados e de armazenamento que podem ser usados no Visual Studio. As ofertas de [Microsoft Azure](https://azure.microsoft.com/) são serviços de dados que incluem todo o provisionamento e a administração do armazenamento de dados subjacente. A carga de trabalho de **desenvolvimento do Azure** no [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) permite que você trabalhe com armazenamentos de dados do Azure diretamente do Visual Studio.
::: moniker-end

![Carga de trabalho de desenvolvimento do Azure](media/azure-development-workload.png)

A maioria dos outros produtos de banco de dados SQL e NoSQL listados aqui pode ser hospedada em um computador local, em uma rede local ou em Microsoft Azure em uma máquina virtual. Se você hospedar o banco de dados em uma máquina virtual Microsoft Azure, você será responsável por gerenciar o próprio banco de dados.

**Microsoft Azure**

- Banco de Dados SQL
- Azure Cosmos DB
- Armazenamento (BLOBs, tabelas, filas, arquivos)
- SQL Data Warehouse
- SQL Server Stretch Database
- StorSimple
- E muito mais…

**SQL**

- SQL Server 2005-2016 (inclui Express e LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- E muito mais…

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB |
- RavenDB
- VelocityDB
- E muito mais…

::: moniker range="vs-2017"

Muitos fornecedores de banco de dados e terceiros dão suporte à integração do Visual Studio por pacotes NuGet. Você pode explorar as ofertas em NuGet.org ou por meio do Gerenciador de pacotes NuGet no Visual Studio ( **ferramentas**  >  **Gerenciador de pacotes NuGet**  >  **gerenciar pacotes NuGet para solução** ). Outros produtos de banco de dados se integram com o Visual Studio como uma extensão. Você pode procurar essas ofertas na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou navegando até **ferramentas**  >  **extensões e atualizações** e, em seguida, selecionando **online** no painel esquerdo da caixa de diálogo. Para obter mais informações, consulte [sistemas de banco de dados compatíveis para o Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Muitos fornecedores de banco de dados e terceiros dão suporte à integração do Visual Studio por pacotes NuGet. Você pode explorar as ofertas em NuGet.org ou por meio do Gerenciador de pacotes NuGet no Visual Studio ( **ferramentas**  >  **Gerenciador de pacotes NuGet**  >  **gerenciar pacotes NuGet para solução** ). Outros produtos de banco de dados se integram com o Visual Studio como uma extensão. Você pode procurar essas ofertas na [Visual Studio Marketplace](https://marketplace.visualstudio.com/) ou navegando até **extensões**  >  **gerenciar extensões** e, em seguida, selecionando **online** no painel esquerdo da caixa de diálogo. Para obter mais informações, consulte [sistemas de banco de dados compatíveis para o Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> O suporte estendido para o SQL Server 2005 terminou em 12 de abril de 2016. Não há nenhuma garantia de que as ferramentas de dados no Visual Studio 2015 e posteriores continuarão a funcionar com o SQL Server 2005. Para obter mais informações, consulte o [anúncio do fim do suporte para o SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Linguagens .NET

Todo o acesso a dados do .NET, incluindo o .NET Core, é baseado em ADO.NET, um conjunto de classes que define uma interface para acessar qualquer tipo de fonte de dados, relacional e não relacional. O Visual Studio tem várias ferramentas e designers que funcionam com o ADO.NET para ajudá-lo a se conectar a bancos de dados, manipular e apresentar os dados para o usuário. A documentação nesta seção descreve como usar essas ferramentas. Você também pode programar diretamente em relação aos objetos de comando ADO.NET. Para obter mais informações sobre como chamar as APIs ADO.NET diretamente, consulte [ADO.net](/dotnet/framework/data/adonet/index).

Para obter a documentação de acesso a dados relacionada ao ASP.NET, consulte [trabalhando com dados](https://www.asp.net/web-forms/overview/presenting-and-managing-data) no site do ASP.net. Para obter um tutorial sobre como usar Entity Framework com o ASP.NET MVC, confira [introdução com Entity Framework 6 Code First usando o MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Os aplicativos Plataforma Universal do Windows (UWP) em C# ou Visual Basic podem usar o SDK do Microsoft Azure para .NET para acessar o armazenamento do Azure e outros serviços do Azure. A classe Windows. Web. HttpClient permite a comunicação com qualquer serviço RESTful. Para obter mais informações, consulte [como se conectar a um servidor http usando Windows. Web. http](/previous-versions/windows/apps/dn469430(v=win.10)).

Para o armazenamento de dados no computador local, a abordagem recomendada é usar o SQLite, que é executado no mesmo processo que o aplicativo. Se uma camada de ORM (mapeamento relacional de objeto) for necessária, você poderá usar Entity Framework. Para obter mais informações, consulte [acesso a dados](/windows/uwp/data-access/index) no Windows Developer Center.

Se você estiver se conectando aos serviços do Azure, certifique-se de baixar as ferramentas mais recentes do [SDK do Azure](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Provedores de dados

Para que um banco de dados seja consumível em ADO.NET, ele deve ter um provedor personalizado de *ADO.net* ou mais deve expor uma interface ODBC ou OLE DB. A Microsoft fornece uma [lista de provedores de dados ADO.net](/dotnet/framework/data/adonet/ado-net-overview) para produtos SQL Server, bem como provedores de OLE DB e ODBC.

### <a name="data-modeling"></a>Modelagem de dados

No .NET, você tem três opções para modelar e manipular dados na memória depois de recuperá-los de uma fonte de dados:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) A tecnologia de ORM da Microsoft preferida. Você pode usá-lo para programar em dados relacionais como objetos do .NET de primeira classe. Para novos aplicativos, deve ser a primeira opção padrão quando um modelo é necessário. Ele requer suporte personalizado do provedor de ADO.NET subjacente.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Um mapeador relacional de objeto de geração anterior. Ele funciona bem para cenários menos complexos, mas não está mais no desenvolvimento ativo.

[Conjuntos](../data-tools/dataset-tools-in-visual-studio.md) de os O mais antigo das três tecnologias de modelagem. Ele foi projetado principalmente para o desenvolvimento rápido de aplicativos de "formulários em dados" nos quais você não está processando grandes quantidades de dados ou realizando consultas ou transformações complexas. Um objeto DataSet consiste em objetos DataTable e DataRow que se assemelham logicamente a objetos do banco de dados SQL muito mais do que objetos .NET. Para aplicativos relativamente simples com base em fontes de dados SQL, os DataSets ainda podem ser uma boa opção.

Não há nenhum requisito para usar nenhuma dessas tecnologias. Em alguns cenários, especialmente onde o desempenho é crítico, você pode simplesmente usar um objeto DataReader para ler do banco de dados e copiar os valores necessários para um objeto de coleção, como List \<T> .

## <a name="native-c"></a>C++ nativo

Os aplicativos C++ que se conectam ao SQL Server devem usar o [driver ODBC do Microsoft® 13,1 para SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) na maioria dos casos. Se os servidores estiverem vinculados, OLE DB será necessário e para que você use o [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Você pode acessar outros bancos de dados usando os drivers [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017&preserve-view=true) ou OLE DB diretamente. O ODBC é a interface de banco de dados padrão atual, mas a maioria dos sistemas de banco de dados fornece uma funcionalidade personalizada que não pode ser acessada pela interface ODBC. OLE DB é uma tecnologia de acesso a dados COM herdada que ainda é suportada, mas não é recomendada para novos aplicativos. Para obter mais informações, consulte [acesso a dados em Visual C++](/cpp/data/data-access-in-cpp).

Os programas C++ que consomem serviços REST podem usar o [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programas C++ que funcionam com Armazenamento do Microsoft Azure podem usar o [cliente armazenamento do Microsoft Azure](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

A modelagem &mdash; de dados do Visual Studio não fornece uma camada de ORM para C++. O [ODB](https://www.codesynthesis.com/products/odb/) é um popular ORM de código-fonte aberto para C++.

Para saber mais sobre como se conectar a bancos de dados de aplicativos C++, consulte [Visual Studio Data Tools para C++](../data-tools/visual-studio-data-tools-for-cpp.md). Para obter mais informações sobre as tecnologias de acesso a dados herdadas Visual C++, consulte [acesso a dados](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

O [JavaScript no Visual Studio](/scripting/javascript/javascript-language-reference) é uma linguagem de primeira classe para a criação de aplicativos de plataforma cruzada, aplicativos UWP, serviços de nuvem, sites e aplicativos Web. Você pode usar Bower, grunt, Gulp, NPM e NuGet de dentro do Visual Studio para instalar suas bibliotecas JavaScript favoritas e seus produtos de banco de dados. Conecte-se ao armazenamento do Azure e aos serviços baixando SDKs do [site do Azure](https://azure.microsoft.com/). Edge.js é uma biblioteca que conecta JavaScript do lado do servidor (Node.js) a fontes de dados ADO.NET.

## <a name="python"></a>Python

Instale o [suporte do Python no Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) para criar aplicativos Python. A documentação do Azure tem vários tutoriais sobre como se conectar a dados, incluindo o seguinte:

- [Django e banco de dados SQL no Azure](/azure/app-service/app-service-web-get-started-python)
- [Django e MySQL no Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Trabalhe com [BLOBs](/azure/storage/blobs/storage-quickstart-blobs-python), [arquivos](/azure/storage/files/storage-python-how-to-use-file-storage), [filas](/azure/storage/queues/storage-python-how-to-use-queue-storage)e [tabelas (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Tópicos relacionados

Plataforma de ia da [Microsoft](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Fornece uma introdução à nuvem inteligente da Microsoft, incluindo o Cortana Analytics Suite e suporte para Internet das Coisas.

[Armazenamento do Microsoft Azure](/azure/storage/) &mdash; Descreve o armazenamento do Azure e como criar aplicativos usando BLOBs, tabelas, filas e arquivos do Azure.

[Banco de dados](/azure/sql-database/) &mdash; SQL do Azure Descreve como se conectar ao banco de dados SQL do Azure, um banco de dados relacional como um serviço.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; Descreve as ferramentas que simplificam o design, a exploração, o teste e a implantação de aplicativos e bancos de dados conectados a data.

[ADO.net](/dotnet/framework/data/adonet/index) &mdash; Descreve a arquitetura ADO.NET e como usar as classes ADO.NET para gerenciar dados de aplicativos e interagir com fontes de dados e XML.

[Entity Framework ADO.net](/ef/ef6/) &mdash; Descreve como criar aplicativos de dados que permitem aos desenvolvedores programar em um modelo conceitual em vez de diretamente em relação a um banco de dados relacional.

[WCF Data Services 4,5](/dotnet/framework/data/wcf/index) &mdash; Descreve como usar [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] o para implantar serviços de dados na Web ou em uma intranet que implementam o [protocolo Open Data (OData)](https://www.odata.org/).

[Dados em soluções](../vsto/data-in-office-solutions.md) &mdash; do Office Contém links para tópicos que explicam como os dados funcionam em soluções do Office. Isso inclui informações sobre programação orientada a esquema, cache de dados e acesso a dados no servidor.

[LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/) &mdash; Descreve os recursos de consulta incorporados ao C# e Visual Basic, e o modelo comum para consultar bancos de dados relacionais, documentos XML, DataSets e coleções na memória.

[Ferramentas XML no Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; Discute o trabalho com dados XML, depuração XSLT, recursos XML do .NET e a arquitetura da consulta XML.

[Documentos e dados XML](/dotnet/standard/data/xml/index) &mdash; Fornece uma visão geral de um conjunto abrangente e integrado de classes que funcionam com documentos e dados XML no .NET.