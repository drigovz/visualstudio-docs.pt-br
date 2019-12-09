---
title: Ferramentas do Modelo de Dados de Entidade
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672388"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Ferramentas de modelo de dados de entidade no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework é uma tecnologia de mapeamento relacional de objeto que permite que os desenvolvedores do .NET trabalhem com dados relacionais usando objetos específicos de domínio. Elimina a necessidade da maioria do código de acesso a dados que os desenvolvedores geralmente precisam gravar. Entity Framework é a tecnologia de modelagem de ORM (mapeamento relacional de objeto) recomendada para novos aplicativos .NET.

 A partir de março de 2016, a versão de lançamento mais recente é [Entity Framework 6](https://msdn.microsoft.com/data/ef) . O [Entity Framework 7](https://docs.efproject.net/en/latest/) está em pré-lançamento.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] ferramentas foram projetadas para ajudá-lo a criar [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplicativos. A documentação completa para [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] ferramentas está aqui: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Com as ferramentas de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], você pode criar um *modelo conceitual* a partir de um banco de dados existente e, em seguida, Visualizar graficamente e editar seu modelo conceitual. Ou, você pode criar graficamente um modelo conceitual primeiro e, em seguida, gerar um banco de dados que dê suporte ao seu modelo. Em ambos os casos, você pode atualizar automaticamente seu modelo quando o banco de dados subjacente é alterado e gerar automaticamente o código de camada de objeto para seu aplicativo. A geração de banco de dados e a geração de código de camada de objeto são personalizáveis.

 Estas são as ferramentas específicas que compõem Modelo de Dados de Entidade ferramentas no Visual Studio 2015:

- Você pode usar o [!INCLUDE[vstecado](../includes/vstecado-md.md)] **Designer de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** (**Entity designer**) para criar e modificar visualmente entidades, associações, mapeamentos e relações de herança. O **Entity designer** também gera [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] ou [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] código de camada de objeto.

- Você pode usar o **Assistente de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** para gerar um modelo conceitual a partir de um banco de dados existente e adicionar informações de conexão de banco de dados ao seu aplicativo.

- Você pode usar o **Assistente para criar banco de dados** para criar um modelo conceitual primeiro e, em seguida, criar um banco de dados que ofereça suporte ao modelo.

- Você pode usar o **Assistente de atualização de modelo** para atualizar seu modelo conceitual, o modelo de armazenamento e os mapeamentos quando forem feitas alterações no banco de dados subjacente.

  > [!NOTE]
  > A partir do Visual Studio 2010, as ferramentas de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] não dão suporte a [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  As ferramentas geram ou modificam um arquivo. edmx. Esse arquivo contém informações que descrevem o modelo conceitual, o modelo de armazenamento e os mapeamentos entre eles. Para obter mais informações, consulte [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools ajuda você a criar aplicativos que usam o Modelo de Dados de Entidade. As ferramentas podem gerar um modelo conceitual, validar um modelo existente, produzir arquivos de código-fonte que contêm classes de objeto com base no modelo conceitual e produzir arquivos de código-fonte que contêm exibições geradas pelo modelo. Para obter informações detalhadas, consulte [exibições de mapeamento geradas previamente](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Entity Framework do ADO.NET](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Descreve como usar as ferramentas de [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], que o [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] fornece, para criar aplicativos.|
|[Modelo de Dados de Entidade](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Fornece links e informações para trabalhar com dados que são usados por aplicativos criados em [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Introdução no .NET completo (console, WinForms, WPF, etc.)](/ef/ef6/get-started)|Fornece tutoriais sobre como criar aplicativos de área de trabalho .NET que usam o Entity Framework 7.|
|[ASP.NET 5 aplicativo para novo banco de dados](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Descreve como criar um novo aplicativo ASP.NET 5 usando o Entity Framework 7.|

## <a name="see-also"></a>Consulte também
 [Ferramentas de dados do Visual Studio para .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
