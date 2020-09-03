---
title: Ferramentas de dados do Visual Studio para .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670094"
---
# <a name="visual-studio-data-tools-for-net"></a>Ferramentas de dados do Visual Studio para .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio e o .NET Framework juntos fornecem amplo suporte de API e ferramentas para conectar-se a bancos de dados, modelar os dados na memória e exibir os dados na interface do usuário.  As classes de .NET Framework que fornecem a funcionalidade de acesso a dados são conhecidas como [ADO.net](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). O ADO.NET, juntamente com as ferramentas de dados no Visual Studio, foi originalmente projetado principalmente para dar suporte a bancos de dados relacionais e XML. Atualmente, muitos fornecedores de banco de dados NoSQL ou terceiros oferecem provedores de ADO.NET.

 O Visual Studio 2015 atualização 2 inclui as atualizações mais recentes do            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), que habilitam o suporte para os recursos mais recentes no [banco de dados SQL](https://azure.microsoft.com/services/sql-database/) do Azure e [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). O [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) dá suporte a ADO.net, exceto para conjuntos de valores e tipos relacionados. Se você estiver direcionando o .NET Core e exigir uma camada de ORM (mapeamento relacional de objeto), use [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 O diagrama a seguir mostra uma visão simplificada da arquitetura básica:

 ![Arquitetura do ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagrama de arquitetura do raddata ADO.NET")

 O fluxo de trabalho típico é o seguinte:

1. Instale um banco de dados de desenvolvimento ou de teste no computador local. Consulte [instalando sistemas de banco de dados, ferramentas e exemplos](../data-tools/installing-database-systems-tools-and-samples.md). Se você estiver usando um serviço de dados do Azure, essa etapa não será necessária.

2. Teste a conexão com o banco de dados (ou o serviço ou arquivo local) no Visual Studio. Consulte [adicionar novas conexões](../data-tools/add-new-connections.md).

3. Adicional Use as ferramentas para gerar e configurar um novo modelo. Modelos baseados em Entity Framework são a recomendação padrão para novos aplicativos. O modelo, seja qual for o que você usa, é a fonte de dados com a qual o aplicativo interage. O modelo fica logicamente entre o banco de dados ou o serviço e o aplicativo.  Consulte [adicionar novas fontes de dados](../data-tools/add-new-data-sources.md).

4. Arraste a fonte de dados da janela **fontes de dados** para um Windows Forms, ASP.NET ou Windows Presentation Foundation superfície de design para gerar o código de vinculação de dados que exibirá os dados para o usuário da maneira que você especificar. Consulte [ligar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Adicione código personalizado para coisas como regras de negócio, pesquisa e validação de dados, ou para aproveitar a funcionalidade personalizada que o Database subjacente expõe.

   Você pode ignorar a etapa 3 e programar um aplicativo .NET para emitir comandos diretamente para um banco de dados, em vez de usar um modelo. Nesse caso, você encontrará a documentação relevante aqui: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Observe que você ainda pode usar o assistente de configuração da fonte de dados e designers para gerar código de vinculação de dados quando você preenche seus próprios objetos na memória e os controles de interface do usuário de ligação de dados com esses objetos.

## <a name="in-this-section"></a>Nesta seção

- [Criar um aplicativo de dados simples usando o ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Adicionar novas conexões](../data-tools/add-new-connections.md)

- [Adicionar novas fontes de dados](../data-tools/add-new-data-sources.md)

- [Ferramentas do Modelo de Dados de Entidade no Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Ferramentas de LINQ to SQL no Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Recursos adicionais para solucionar problemas de erros de acesso a dados](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Serviços do Windows Communication Foundation e WCF Data Services no Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Criando e gerenciando bancos de dados e aplicativos da camada de dados no Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Recursos adicionais para solucionar problemas de erros de acesso a dados](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Consulte Também
 [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
