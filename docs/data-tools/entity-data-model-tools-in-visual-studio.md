---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6efcd0ca4e8274df7667b5a5b2b75020def8c358
ms.sourcegitcommit: 8589d85cc10710ef87e6363a2effa5ee5610d46a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72807021"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools no Visual Studio

Entity Framework é uma tecnologia de mapeamento relacional de objeto que permite que os desenvolvedores do .NET trabalhem com dados relacionais usando objetos específicos de domínio. Elimina a necessidade da maioria do código de acesso a dados que os desenvolvedores geralmente precisam gravar. Entity Framework é a tecnologia de modelagem de ORM (mapeamento relacional de objeto) recomendada para novos aplicativos .NET.

Entity Framework Tools são projetadas para ajudá-lo a criar aplicativos de Entity Framework (EF). A documentação completa para Entity Framework está aqui: [visão geral – EF 6](/ef/ef6/).

  > [!NOTE]
  > O Entity Framework Tools descrito nesta página é usado para gerar arquivos *. edmx* , que não têm suporte no EF Core. Para gerar um modelo de EF Core de um banco de dados existente, consulte [engenharia reversa-EF Core](/ef/core/managing-schemas/scaffolding). Para obter mais informações sobre as diferenças entre o EF 6 e o EF Core, consulte [comparar o EF 6 e o EF Core](/ef/efcore-and-ef6/).

Com Entity Framework Tools, você pode criar um *modelo conceitual* a partir de um banco de dados existente e, em seguida, Visualizar graficamente e editar seu modelo conceitual. Ou, você pode criar graficamente um modelo conceitual primeiro e, em seguida, gerar um banco de dados que dê suporte ao seu modelo. Em ambos os casos, você pode atualizar automaticamente seu modelo quando o banco de dados subjacente é alterado e gerar automaticamente o código de camada de objeto para seu aplicativo. A geração de banco de dados e a geração de código de camada de objeto são personalizáveis.

As ferramentas de Entity Framework são instaladas como parte da carga de trabalho de **processamento e armazenamento de dados** no instalador do Visual Studio. Você também pode instalá-los como um componente individual na categoria **SDKs, bibliotecas e estruturas** .

Essas são as ferramentas específicas que compõem Entity Framework ferramentas no Visual Studio:

- Você pode usar o [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **Designer de[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** (**Entity designer**) para criar e modificar visualmente entidades, associações, mapeamentos e relações de herança. O **Entity designer** também gera [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] ou [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] código de camada de objeto.

- Você pode usar o **Assistente de[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** para gerar um modelo conceitual a partir de um banco de dados existente e adicionar informações de conexão de banco de dados ao seu aplicativo.

- Você pode usar o **Assistente para criar banco de dados** para criar um modelo conceitual primeiro e, em seguida, criar um banco de dados que ofereça suporte ao modelo.

- Você pode usar o **Assistente de atualização de modelo** para atualizar seu modelo conceitual, o modelo de armazenamento e os mapeamentos quando forem feitas alterações no banco de dados subjacente.

  > [!NOTE]
  > A partir do Visual Studio 2010, as ferramentas de Entity Framework não dão suporte a [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

As ferramentas geram ou modificam um arquivo *. edmx* . Esse arquivo *. edmx* contém informações que descrevem o modelo conceitual, o modelo de armazenamento e os mapeamentos entre eles. Para obter mais informações, consulte [edmx](/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) ajuda você a criar aplicativos que usam o modelo de dados de entidade. O Power Tools pode gerar um modelo conceitual, validar um modelo existente, produzir arquivos de código-fonte que contêm classes de objeto com base no modelo conceitual e produzir arquivos de código-fonte que contenham exibições geradas pelo modelo. Para obter informações detalhadas, consulte [exibições de mapeamento geradas previamente](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Tópicos relacionados

| Título | Descrição |
| - | - |
| [Entity Framework do ADO.NET](/dotnet/framework/data/adonet/ef/index) | Descreve como usar as ferramentas de [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], que o [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fornece, para criar aplicativos. |
| [Modelo de Dados de Entidade](/dotnet/framework/data/adonet/entity-data-model) | Fornece links e informações para trabalhar com dados que são usados por aplicativos criados em [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Documentação do Entity Framework (EF))](/ef/ef6/get-started) | Fornece um índice de vídeos, tutoriais e documentação avançada para ajudá-lo a aproveitar ao máximo Entity Framework. |
| [ASP.NET 5 aplicativo para novo banco de dados](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Descreve como criar um novo aplicativo ASP.NET 5 usando o Entity Framework 7. |

## <a name="see-also"></a>Consulte também

- [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)