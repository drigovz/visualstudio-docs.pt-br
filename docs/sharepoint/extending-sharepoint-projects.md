---
title: Estendendo projetos do SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [SharePoint development in Visual Studio], extending
- SharePoint development in Visual Studio, extending projects
- SharePoint projects, extending
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6bc92d65ed179c7f2cb2f569a7d254a025887845
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62967475"
---
# <a name="extend-sharepoint-projects"></a>Estender projetos do SharePoint
  Crie uma extensão de projeto quando desejar personalizar os recursos de nível de projeto dos projetos do SharePoint. Por exemplo, você pode adicionar propriedades de projeto personalizadas ou responder a eventos de nível de projeto que são gerados quando o usuário desenvolve uma solução do SharePoint no Visual Studio.

## <a name="create-project-extensions"></a>Criar extensões de projeto
 Para estender um item de projeto, crie um assembly de extensão do Visual Studio que implementa a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension> interface. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

 Ao criar uma extensão de projeto, você também pode adicionar a seguinte funcionalidade aos projetos do SharePoint:

- Adicione um item de menu de atalho. O item de menu aparece quando você abre o menu de atalho para um nó de projeto do SharePoint no **Gerenciador de soluções** clicando com o botão direito do mouse no nó ou escolhendo-o e escolhendo as teclas **Shift** + **F10** . Para obter mais informações, consulte [como adicionar um item de menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md).

- Adicione uma propriedade personalizada. A propriedade aparece na janela **Propriedades** quando você escolhe um projeto do SharePoint no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md).

  Para obter instruções que demonstram como criar, implantar e testar uma extensão de projeto, consulte [passo a passos: criar uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md).

## <a name="understand-the-relationship-between-project-extensions-and-project-instances"></a>Entender a relação entre as extensões de projeto e as instâncias de projeto
 Quando você cria uma extensão de projeto, a extensão é carregada quando qualquer tipo de projeto do SharePoint é aberto no [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] inclui vários modelos de projeto do SharePoint, como definições de lista, tipos de conteúdo e receptores de eventos. No entanto, há apenas um tipo de projeto do SharePoint. Os tipos de projeto que aparecem na caixa de diálogo **novo projeto** são apenas modelos que agrupam um ou mais itens de projeto do SharePoint. Como há apenas um tipo de projeto do SharePoint, as extensões criadas para um projeto se aplicam a todos os projetos do SharePoint. Você não pode, por exemplo, criar uma extensão que se aplica a apenas um projeto de **tipo de conteúdo** .

 Para acessar uma instância de projeto específica, manipule um dos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents> eventos do parâmetro *ProjectService* em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectExtension.Initialize%2A> método. Por exemplo, para determinar quando um projeto do SharePoint é adicionado a uma solução, manipule o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento. Para obter mais informações, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Confira também
- [Como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)
- [Como: adicionar um item de menu de atalho a projetos do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-sharepoint-projects.md)
- [Como: adicionar uma propriedade a projetos do SharePoint](../sharepoint/how-to-add-a-property-to-sharepoint-projects.md)
- [Walkthrough: criar uma extensão de projeto do SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-project-extension.md)
- [Definir tipos de item de projeto personalizados do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [Estender itens de projeto do SharePoint](../sharepoint/extending-sharepoint-project-items.md)
- [Estender o empacotamento e a implantação do SharePoint](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
