---
title: Trabalhar com conjuntos de itens em aplicativos de n camadas | Microsoft Docs
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657812"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>Trabalhar com conjuntos de dados em aplicativos de n camadas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os aplicativos de dados de N camadas * são aplicativos centrados em dados que são separados em várias camadas lógicas (ou *camadas*). Em outras palavras, um aplicativo de dados de N camadas é um aplicativo separado em vários projetos, com camada de acesso a dados, camada lógica de negócios e camada de apresentação em seu próprio projeto. Para obter mais informações, consulte [visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md).

 Os conjuntos de dados tipados foram aprimorados para que as classes TableAdapters e de conjuntos de dados possam ser geradas em projetos discretos. Com isso, é possível separar com rapidez as camadas de aplicativos e gerar aplicativos de dados de N camadas.

 O suporte de N camadas em datasets tipados permite o desenvolvimento iterativo da arquitetura do aplicativo para um design de n camadas. Ele também remove a necessidade de separar manualmente o código em mais de um projeto. Comece a criar a camada de dados usando o Designer de Conjunto de Dados. Quando você estiver pronto para aplicar a arquitetura do aplicativo a um projeto de N camadas, configure a propriedade **Projeto de Conjunto de Dados** de um conjunto de dados para gerar a classe do conjunto de dados em um projeto separado.

## <a name="in-this-section"></a>Nesta seção
 [Separar conjuntos de linhas e TableAdapters em projetos diferentes](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) Descreve como mover a classe DataSet gerada para fora do projeto que contém as classes do TableAdapter geradas e para um novo projeto.

 [Adicionar código a TableAdapters em aplicativos de n camadas](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) Descreve como gerar uma classe parcial na qual o código pode ser adicionado a um TableAdapter de n camadas.

 [Adicionar código a conjuntos de itens em aplicativos de n camadas](../data-tools/add-code-to-datasets-in-n-tier-applications.md) Descreve como gerar uma classe parcial na qual o código pode ser adicionado a um conjunto de uma de n camadas.

 [Adicionar validação a um conjunto de um DataSet de n camadas](../data-tools/add-validation-to-an-n-tier-dataset.md) Descreve onde adicionar código para executar a validação em dados de alteração.

 [Walkthrough: Criando um aplicativo de dados de N camadas](../data-tools/walkthrough-creating-an-n-tier-data-application.md) Fornece instruções passo a passo para criar um conjunto de um dataset tipado e separar o TableAdapter e o código do conjunto de informações em vários projetos.

 [Walkthrough: adicionando validação a um aplicativo de dados de N camadas](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) Fornece instruções passo a passo para a adição de validação ao aplicativo que foi criado na explicação do aplicativo de dados de n camadas.

## <a name="reference"></a>Referência
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>Seções relacionadas

- [Visão geral de aplicativos de dados de N camadas](../data-tools/n-tier-data-applications-overview.md)
- [Atualização hierárquica](../data-tools/hierarchical-update.md)
- [Ferramentas de conjunto de dados no Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Acessando dados no Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [Aplicativos de n camadas e remoto com LINQ to SQL](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)