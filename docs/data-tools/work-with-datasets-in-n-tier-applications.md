---
title: Trabalhar com conjuntos de dados em aplicativos de n camadas
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: b96f2e51048216388eea50935a1ced536d8d230b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648026"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabalhar com conjuntos de dados em aplicativos de n camadas

Os *aplicativos de dados de N camadas* são aplicativos centrados em dados que são separados em várias camadas lógicas (ou apenas *camadas*). Em outras palavras, um aplicativo de dados de N camadas é um aplicativo separado em vários projetos, com camada de acesso a dados, camada lógica de negócios e camada de apresentação em seu próprio projeto. Para obter mais informações, consulte [visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).

Os conjuntos de dados tipados foram aprimorados para que as classes TableAdapters e de conjuntos de dados possam ser geradas em projetos discretos. Com isso, é possível separar com rapidez as camadas de aplicativos e gerar aplicativos de dados de N camadas.

O suporte de N camadas em datasets tipados permite o desenvolvimento iterativo da arquitetura do aplicativo para um design de n camadas. Ele também remove a necessidade de separar manualmente o código em mais de um projeto. Comece a criar a camada de dados usando o **Designer de conjunto de dados**. Quando você estiver pronto para aplicar a arquitetura do aplicativo a um projeto de N camadas, configure a propriedade **Projeto de Conjunto de Dados** de um conjunto de dados para gerar a classe do conjunto de dados em um projeto separado.

## <a name="reference"></a>Referência

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>Consulte também

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Passo a passo: criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Adicionar código a TableAdapters em aplicativos de N camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [Como adicionar código a conjuntos de dados em aplicativos de N camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Adicionar validação a um conjunto de dados de N camadas](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [Separar conjuntos de dados e TableAdapters em diferentes projetos](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [Atualização hierárquica](../data-tools/hierarchical-update.md)
- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Criar e configurar TableAdapters](../data-tools/create-and-configure-tableadapters.md)
- [Aplicativos de N camadas e remotos com o LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)