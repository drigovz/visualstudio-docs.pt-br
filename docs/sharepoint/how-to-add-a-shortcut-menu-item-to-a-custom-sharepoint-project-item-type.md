---
title: Adicionar item de menu de atalho para o tipo de item de projeto personalizado do SharePoint
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
ms.openlocfilehash: 95c47cdc00fc9035870aed4ac2e0bee4d3c1c5af
ms.sourcegitcommit: 25570fb5fb197318a96d45160eaf7def60d49b2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66401631"
---
# <a name="how-to-add-a-shortcut-menu-item-to-a-custom-sharepoint-project-item-type"></a>Como: Adicionar um item de menu de atalho para um tipo de item de projeto personalizado do SharePoint
  Quando você define um tipo de item de projeto personalizado do SharePoint, você pode adicionar um item de menu de atalho para o item de projeto. O item de menu é exibido quando um usuário clica o item de projeto no **Gerenciador de soluções**.

 As etapas a seguir pressupõem que você já definiu seu próprio tipo de item de projeto do SharePoint. Para obter mais informações, confira [Como: Definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md).

### <a name="to-add-a-shortcut-menu-item-to-a-custom-project-item-type"></a>Para adicionar um item de menu de atalho para um tipo de item de projeto personalizado

1. No <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider.InitializeType%2A> método de seu <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemTypeProvider> implementação, o identificador a <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento do *projectItemTypeDefinition* parâmetro.

2. No manipulador de eventos para o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemEvents.ProjectItemMenuItemsRequested> evento, adicione um novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto para o <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.ViewMenuItems%2A> ou <xref:Microsoft.VisualStudio.SharePoint.SharePointProjectItemMenuItemsRequestedEventArgs.AddMenuItems%2A> coleção do parâmetro de argumentos de evento.

3. No <xref:Microsoft.VisualStudio.SharePoint.IMenuItem.Click> manipulador de eventos para o novo <xref:Microsoft.VisualStudio.SharePoint.IMenuItem> do objeto, execute as tarefas que você deseja executar quando um usuário escolhe o item de menu de atalho.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir demonstra como adicionar um item de menu de contexto para um tipo de item de projeto personalizado. Quando o usuário abre o menu de atalho do item de projeto **Gerenciador de soluções** e escolhe o **mensagem de gravação para a janela de saída** item de menu, o Visual Studio exibe uma mensagem no **saída**  janela.

 [!code-csharp[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/CSharp/projectitemmenuandproperty/extension/projectitemtypemenu.cs#4)]
 [!code-vb[SPExtensibility.ProjectItemExtension.MenuAndProperty#4](../sharepoint/codesnippet/VisualBasic/projectitemmenuandproperty/extension/projectitemtypemenu.vb#4)]

 Este exemplo usa o serviço de projeto do SharePoint para gravar a mensagem para o **saída** janela. Para obter mais informações, consulte [usar o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md).

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer um projeto de biblioteca de classes com as referências aos assemblies a seguir:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-project-item"></a>Implantar o item de projeto
 Para habilitar outros desenvolvedores a usar o item de projeto, crie um modelo de projeto ou um modelo de item de projeto. Para obter mais informações, consulte [criar um item modelos e modelos de projeto do SharePoint para itens de projeto](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

 Para implantar o item de projeto, crie um [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] extensão (VSIX) do pacote para o assembly, o modelo e os outros arquivos que você deseja distribuir com o item de projeto. Para obter mais informações, consulte [implantar extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte também
- [Como: Definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)
- [Como: Adicionar uma propriedade a um tipo de item de projeto personalizado do SharePoint](../sharepoint/how-to-add-a-property-to-a-custom-sharepoint-project-item-type.md)
- [Definindo tipos personalizados de item de projeto do SharePoint](../sharepoint/defining-custom-sharepoint-project-item-types.md)
