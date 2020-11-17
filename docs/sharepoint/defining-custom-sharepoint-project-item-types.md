---
title: Definindo tipos de item de projeto personalizados do SharePoint | Microsoft Docs
description: Defina um tipo de item de projeto do SharePoint personalizado quando desejar criar um novo tipo de item de projeto do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project items, defining your own types
- project items [SharePoint development in Visual Studio], defining your own types
- SharePoint development in Visual Studio, defining new project item types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fc2e3670dd734b368795f270fa6c1d63c8c079e8
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672828"
---
# <a name="define-custom-sharepoint-project-item-types"></a>Definir tipos de item de projeto personalizados do SharePoint
  Defina um novo tipo de item de projeto do SharePoint quando desejar criar um novo tipo de item de projeto do SharePoint. Por exemplo, o Visual Studio não inclui itens de projeto do SharePoint para adicionar campos ou ações personalizadas a um site do SharePoint. Você pode definir seus próprios tipos de itens de projeto do SharePoint para criar campos, ações personalizadas ou outros tipos de componentes do SharePoint.

## <a name="tasks-for-defining-sharepoint-project-item-types"></a>Tarefas para definir tipos de item de projeto do SharePoint
 Para definir um tipo de item de projeto personalizado, crie um assembly de extensão do Visual Studio que implementa a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> interface. Para obter mais informações, consulte [como: definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

 Ao definir um tipo de item de projeto personalizado, você também pode adicionar a seguinte funcionalidade ao item de projeto:

- Adicione um item de menu de atalho ao item de projeto. O item de menu aparece quando você abre o menu de atalho para o item de projeto no **Gerenciador de soluções** clicando com o botão direito do mouse no item do projeto ou escolhendo-o e escolhendo as teclas **Shift** + **F10** . Para obter mais informações, consulte [como: adicionar um item de menu de atalho a um tipo personalizado de item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md).

- Adicione uma propriedade personalizada ao item de projeto. A propriedade aparece na janela **Propriedades** quando você escolhe o item de projeto no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a um tipo de item de projeto personalizado do SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md).

  Para permitir que outros desenvolvedores usem seu item de projeto no Visual Studio, crie um arquivo. COMDATA e crie um modelo de item ou de projeto associado ao item de projeto. Para obter mais informações, consulte [criar modelos de item e modelos de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="understand-the-relationship-between-project-item-types-and-project-item-instances"></a>Entender a relação entre tipos de item de projeto e instâncias de item de projeto
 Quando você define um tipo de item de projeto do SharePoint, o Visual Studio carrega sua extensão quando um item de projeto do tipo associado é adicionado a um projeto do SharePoint. Por exemplo, se você definir um novo tipo de item de projeto de **ação personalizada** , o Visual Studio carregará sua extensão quando um usuário adicionar um item de projeto de **ação personalizada** a um projeto. O Visual Studio usa a mesma instância de sua extensão para todas as instâncias do tipo de item de projeto associado. No exemplo anterior, se o usuário adicionar um segundo item de projeto de **ação personalizada** ao projeto, a mesma instância de sua extensão será usada para personalizar o segundo item de projeto.

 Para acessar uma instância específica do tipo de item do projeto, manipule um dos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos do parâmetro *projectItemTypeDefinition* em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método. Por exemplo, para determinar quando um item de projeto do tipo personalizado é adicionado a um projeto, manipule o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obter mais informações, consulte [como: definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

## <a name="see-also"></a>Veja também
- [Como definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Como: adicionar uma propriedade a um tipo de item de projeto personalizado do SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Como: adicionar um item de menu de atalho a um tipo personalizado de item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type.md)
- [Criar modelos de item e modelos de projeto para itens de projeto do SharePoint](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md)
- [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)
- [Walkthrough: Criar item de projeto de coluna de site com um modelo de projeto, parte 1](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-1.md)
- [Walkthrough: criar um item de projeto de ação personalizada com um modelo de item, parte 2](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-2.md)
- [Walkthrough: criar um item de projeto de coluna de site com um modelo de projeto, parte 2](../sharepoint/walkthrough-creating-a-site-column-project-item-with-a-project-template-part-2.md)
- [Implantar extensões para as ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
