---
title: Estendendo itens de projeto do SharePoint | Microsoft Docs
description: Examine as tarefas para estender itens de projeto do SharePoint. Entenda como as extensões de item de projeto e as instâncias de item de projeto estão relacionadas.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- project items [SharePoint development in Visual Studio], extending
- SharePoint project items, extending
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 22ba5acb995466e695c0e25b5b7540f3677b1264
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672568"
---
# <a name="extend-sharepoint-project-items"></a>Estender itens de projeto do SharePoint
  Crie uma extensão de item de projeto quando desejar adicionar funcionalidade a um tipo de item de projeto do SharePoint que já está instalado no Visual Studio. Por exemplo, você pode criar uma extensão para o **receptor de evento** interno ou itens de projeto de **definição de lista** no Visual Studio, ou pode criar uma extensão para um tipo de item de projeto personalizado. Você também pode criar uma extensão para todos os tipos de itens de projeto do SharePoint.

## <a name="tasks-for-extending-sharepoint-project-items"></a>Tarefas para estender itens de projeto do SharePoint
 Para estender um item de projeto, crie um assembly de extensão do Visual Studio que implementa a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension> interface. Para obter mais informações, consulte [como: criar uma extensão de item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

 Ao estender um item de projeto, você também pode adicionar a seguinte funcionalidade ao item de projeto:

- Adicione um item de menu de atalho ao item de projeto. O item de menu aparece quando você abre o menu de atalho para o item de projeto no **Gerenciador de soluções**. Abra o menu de atalho clicando com o botão direito do mouse no item do projeto ou escolhendo-o e escolhendo as teclas **Shift** + **F10** . Para obter mais informações, consulte [como: adicionar um item de menu de atalho a uma extensão de item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md).

- Adicione uma propriedade personalizada ao item de projeto. A propriedade aparece na janela **Propriedades** quando você escolhe o item de projeto no **Gerenciador de soluções**. Para obter mais informações, consulte [como: adicionar uma propriedade a uma extensão de item de projeto do SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md).

  Para obter instruções que demonstram como criar, implantar e testar uma extensão de item de projeto, consulte [Walkthrough: estender um tipo de item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md).

## <a name="understand-the-relationship-between-project-item-extensions-and-project-item-instances"></a>Entender a relação entre as extensões de item de projeto e as instâncias de item de projeto
 Quando você cria uma extensão de item de projeto, o Visual Studio carrega sua extensão quando um item de projeto do tipo associado é adicionado a um projeto do SharePoint. Por exemplo, se você criar uma extensão para itens de projeto **receptor de eventos** , o Visual Studio carregará sua extensão quando um usuário adicionar um item de projeto **receptor de evento** a um projeto. O Visual Studio usa a mesma instância de sua extensão para todas as instâncias do tipo de item de projeto associado. No exemplo anterior, se o usuário adicionar um segundo item de projeto **receptor de evento** ao projeto, a mesma instância de sua extensão será usada para personalizar o segundo item de projeto.

 Para acessar uma instância específica do tipo de item de projeto que você está estendendo, manipule um dos <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents> eventos do parâmetro *projectItemType* em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeExtension.Initialize%2A> método. Por exemplo, para determinar quando um item de projeto do tipo que você está estendendo é adicionado a um projeto, manipule o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemAdded> evento. Para obter mais informações, consulte [como: criar uma extensão de item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md).

## <a name="identifiers-for-sharepoint-project-items"></a>Identificadores para itens de projeto do SharePoint
 Cada item de projeto do SharePoint tem um identificador de cadeia de caracteres correspondente. Você deve saber o identificador de um item de projeto se desejar executar as seguintes tarefas:

- Crie uma extensão para o item de projeto. Nesse caso, você deve passar o identificador para o item de projeto que você deseja estender para o construtor do <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemTypeAttribute> . Para criar uma extensão para todos os tipos de item de projeto, passe o **\\** valor de cadeia de caracteres *.

- Adicione o item de projeto a um projeto programaticamente. Nesse caso, você deve passar o identificador do item de projeto para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemCollection.Add%2A> método.

  A tabela a seguir lista os identificadores para os itens de projeto do SharePoint que são incluídos no Visual Studio.

|Nome do item do projeto|Identificador de cadeia de caracteres|
|-----------------------|-----------------------|
|Modelo de catálogo de dados corporativos|Microsoft. VisualStudio. SharePoint. BusinessDataConnectivity|
|Tipo de conteúdo|Microsoft. VisualStudio. SharePoint. ContentType|
|Receptor de eventos|Microsoft. VisualStudio. SharePoint. EventHandler|
|Elemento vazio|Microsoft. VisualStudio. SharePoint. Genericelement|
|Definição de lista<br /><br /> Definição de lista de tipo de conteúdo|Microsoft. VisualStudio. SharePoint. ListDefinition|
|Listar instância|Microsoft. VisualStudio. SharePoint. ListInstance|
|Módulo|Microsoft. VisualStudio. SharePoint. Module|
|Fluxo de trabalho Sequencial<br /><br /> Fluxo de trabalho da máquina de estado|Microsoft. VisualStudio. SharePoint. Workflow|
|Definição de site|Microsoft. VisualStudio. SharePoint. SiteDefinition|
|Web Part Visual|Microsoft. VisualStudio. SharePoint. VisualWebPart|
|Web Part|Microsoft. VisualStudio. SharePoint. WebPart|
|Formulário de associação de fluxo de trabalho|Microsoft. VisualStudio. SharePoint. WorkflowAssociation|

## <a name="see-also"></a>Veja também
- [Como: criar uma extensão de item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)
- [Como: adicionar um item de menu de atalho a uma extensão de item de projeto do SharePoint](../sharepoint/how-to-add-a-shortcut-menu-item-to-a-sharepoint-project-item-extension.md)
- [Como: adicionar uma propriedade a uma extensão de item de projeto do SharePoint](../sharepoint/how-to-add-a-property-to-a-sharepoint-project-item-extension.md)
- [Walkthrough: estender um tipo de item de projeto do SharePoint](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)
- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
