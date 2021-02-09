---
title: Ferramentas do conjunto de dados
description: Examine as ferramentas de conjunto de ferramenta disponíveis no Visual Studio. Leia sobre fluxo de trabalho do conjunto de informações, conjuntos de valores e arquitetura de N camadas e conjuntos de informações e XML.
ms.custom: SEO-VS-2020
ms.date: 11/21/2018
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 4e711d60010117f3a5081470ab8e6e656a7e6e90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866990"
---
# <a name="dataset-tools-in-visual-studio"></a>Ferramentas de conjunto de dados no Visual Studio

> [!NOTE]
> Conjuntos de dados e classes relacionadas são tecnologias .NET herdadas do 2000s inicial que permitem que os aplicativos trabalhem com dados na memória, enquanto os aplicativos são desconectados do banco de dado. Eles são especialmente úteis para aplicativos que permitem aos usuários modificar dados e persistir as alterações de volta para o banco de dado. Embora os conjuntos de aplicativos sejam comprovadamente uma tecnologia bem bem-sucedida, recomendamos que os novos aplicativos .NET usem Entity Framework. O Entity Framework fornece uma maneira mais natural de trabalhar com dados tabulares como modelos de objeto e tem uma interface de programação mais simples.

Um `DataSet` objeto é um objeto na memória que é essencialmente um mini-banco de dados. Ele contém `DataTable` os `DataColumn` objetos, e, `DataRow` nos quais você pode armazenar e modificar dados de um ou mais bancos sem precisar manter uma conexão aberta. O conjunto de dados mantém informações sobre as alterações de seu dado, para que as atualizações possam ser rastreadas e enviadas de volta ao banco de dados quando seu aplicativo for reconectado.

Conjuntos de valores e classes relacionadas são definidos no <xref:System.Data?displayProperty=fullName> namespace na API do .net. Você pode criar e modificar conjuntos de valores dinamicamente no código usando ADO.NET. A documentação nesta seção mostra como trabalhar com conjuntos de valores usando designers do Visual Studio. Os conjuntos de dados que são criados por meio de designers usam objetos **TableAdapter** para interagir com ele. Os conjuntos de valores criados programaticamente usam objetos **DataAdapter** . Para obter informações sobre como criar conjuntos de dados programaticamente, consulte [Dataadaptadores e Datalêrs](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

Se seu aplicativo precisar ler apenas dados de um banco de dado e não executar atualizações, adições ou exclusões, você geralmente pode obter melhor desempenho usando um `DataReader` objeto para recuperar dados em um `List` objeto genérico ou outro objeto de coleção. Se você estiver exibindo os dados, você poderá vincular a interface do usuário à coleção de dados.

## <a name="dataset-workflow"></a>Fluxo de trabalho do DataSet

O Visual Studio fornece ferramentas para simplificar o trabalho com conjuntos de valores. O fluxo de trabalho básico de ponta a ponta é:

- Use a [janela fontes de dados](add-new-data-sources.md#data-sources-window) para criar um novo conjunto de dados a partir de uma ou mais fontes. Use o **Designer de conjunto de dados** para configurar o conjunto de e definir suas propriedades. Por exemplo, você precisa especificar quais tabelas da fonte de dados devem ser incluídas e quais colunas de cada tabela. Escolha atentamente para conservar a quantidade de memória exigida pelo conjunto de um. Para obter mais informações, consulte [Create and configure datasets (Criar e configurar conjuntos de dados)](../data-tools/create-and-configure-datasets-in-visual-studio.md).

- Especifique as relações entre as tabelas para que as chaves estrangeiras sejam manipuladas corretamente. Para obter mais informações, consulte [preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md).

- Use o **Assistente de configuração do TableAdapter** para especificar a consulta ou o procedimento armazenado que popula o conjunto de dados, e quais operações de banco (atualização, exclusão e assim por diante) implementarão. Para saber mais, consulte esses tópicos:

  - [Preencher conjuntos de dados usando TableAdapters](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [Editar dados em conjuntos de dados](../data-tools/edit-data-in-datasets.md)

  - [Validar dados em conjuntos de dados](../data-tools/validate-data-in-datasets.md)

  - [Salvar dados novamente no banco de dados](../data-tools/save-data-back-to-the-database.md)

- Consultar e Pesquisar os dados no DataSet. Para obter mais informações, consulte conjuntos de dados de [consulta](../data-tools/query-datasets.md). [!INCLUDE[linq_dataset](../data-tools/includes/linq_dataset_md.md)] habilita o [LINQ (consulta integrada à linguagem)](/dotnet/csharp/linq/) sobre os dados em um <xref:System.Data.DataSet> objeto. Para obter mais informações, consulte [LINQ to DataSet](/dotnet/framework/data/adonet/linq-to-dataset).

- Use a janela **fontes de dados** para associar controles de interface do usuário ao conjunto de dados ou a suas colunas individuais, e para especificar quais colunas são editáveis pelo usuário. Para obter mais informações, confira [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

## <a name="datasets-and-n-tier-architecture"></a>Conjuntos de valores e arquitetura de N camadas

Para obter informações sobre conjuntos de dados em aplicativos de N camadas, consulte [trabalhar com conjuntos de dados em aplicativos de n camadas](../data-tools/work-with-datasets-in-n-tier-applications.md).

## <a name="datasets-and-xml"></a>Conjuntos de e XML

Para obter informações sobre a conversão de conjuntos de dados de e para XML, consulte [Read XML data to a DataSet](../data-tools/read-xml-data-into-a-dataset.md) e [Save a DataSet as XML](../data-tools/save-a-dataset-as-xml.md).

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
