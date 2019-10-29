---
title: Criando colunas de site, tipos de conteúdo e listas para o SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 538d82794fcecb91e4f13ab6d7718d0bf407b86f
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984510"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Criar colunas de site, tipos de conteúdo e listas para o SharePoint
  O Visual Studio fornece modelos de item de projeto para muitos itens fundamentais do SharePoint diferentes, incluindo *listas* e *tipos de conteúdo*, ambos podem incorporar colunas de site (ou *campos*). Os novos designers para tipos de conteúdo e listas tornam a criação desses itens mais fácil do que nunca.

## <a name="site-columns"></a>Colunas do site
 As colunas do site são um dos elementos mais básicos que você pode adicionar a um projeto do SharePoint. Uma coluna de site representa um tipo de dados, como um número de telefone, um comentário ou o nome da cidade de um contato em uma lista de contatos.

 O novo modelo de item de projeto coluna de site torna a criação de colunas de site mais fácil do que na versão anterior do Visual Studio. Depois de criar uma nova coluna de site, você pode modificar o XML no arquivo *Elements. xml* da coluna do site para incluir as informações desejadas, como seu nome de exibição, seu tipo de dados e o grupo no qual você deseja que a coluna do site apareça no SharePoint. Para obter mais informações sobre colunas de site, consulte [introdução às colunas](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14)).

## <a name="content-types-and-lists"></a>Tipos de conteúdo e listas
 Tipos de conteúdo e listas estão entre os elementos usados com mais frequência no SharePoint.

 Um tipo de conteúdo define os metadados, o fluxo de trabalho e o comportamento de uma categoria de itens em uma lista do SharePoint ou biblioteca de documentos. Por exemplo, você pode criar um tipo de conteúdo para informações em uma lista de contatos ou em uma lista de tarefas. Um tipo de conteúdo de contato pode incluir colunas como nome, email, número de telefone e endereço. Um tipo de conteúdo que você define no nível do site é independente de qualquer lista ou biblioteca de documentos no site. Você pode usar o mesmo tipo de conteúdo com listas ou bibliotecas de documentos diferentes no site do SharePoint. Você também pode usar vários tipos de conteúdo na mesma lista ou biblioteca de documentos.

 Uma lista é uma coleção de informações no SharePoint que você pode compartilhar com outras pessoas. Listas consistem em linhas de colunas que contêm dados. Alguns exemplos de listas incluem: uma lista de tarefas, uma lista de contatos e uma lista de anúncios.

 Os novos tipos de conteúdo e designers de lista no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tornam a criação de tipos e listas de conteúdo de site muito mais fácil e mais intuitiva do que na versão anterior do Visual Studio. A interface do usuário permite que você construa visualmente tipos de conteúdo e listas de forma familiar e permite classificar e agrupar dados em listas e usar títulos de grupo. Para obter mais informações sobre tipos de conteúdo, consulte [tipos de conteúdo](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Para obter mais informações sobre listas, consulte [listar formulários](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) e [exibições de lista](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Walkthrough: criar uma coluna de site, um tipo de conteúdo e uma lista para o SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Demonstra como criar colunas de site que são usadas em um tipo de conteúdo personalizado. O tipo de conteúdo é usado em uma lista personalizada.|

## <a name="see-also"></a>Consulte também
- [Comece a desenvolver no SharePoint 2010](/sharepoint/dev/)
