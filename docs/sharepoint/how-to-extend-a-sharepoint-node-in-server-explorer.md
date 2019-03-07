---
title: 'Como: Estender um nó SharePoint no Gerenciador de servidores | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint Connections [SharePoint development in Visual Studio], extending a node
- SharePoint development in Visual Studio, extending SharePoint Connections node in Server Explorer
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 48b162d3ae4d9eacc5ca227848056672186d1390
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56638914"
---
# <a name="how-to-extend-a-sharepoint-node-in-server-explorer"></a>Como: Estender um nó SharePoint no Gerenciador de servidores
  Você pode estender os nós sob o **conexões do SharePoint** nó no **Gerenciador de servidores**. Isso é útil quando você deseja adicionar novos nós filhos, itens de menu de atalho ou propriedades para um nó existente. Para obter mais informações, consulte [estender o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

### <a name="to-extend-a-sharepoint-node-in-server-explorer"></a>Para estender um nó SharePoint no Gerenciador de servidores

1.  Crie um projeto de biblioteca de classes.

2.  Adicione referências aos assemblies a seguir:

    -   Microsoft.VisualStudio.SharePoint

    -   Microsoft.VisualStudio.SharePoint.Explorer.Extensions

    -   System.ComponentModel.Composition

3.  Crie uma nova classe que implemente a interface <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension>.

4.  Adicionar o <xref:System.ComponentModel.Composition.ExportAttribute> à classe de atributo. Esse atributo permite que o Visual Studio descobrir e carregar seu <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> implementação. Passar o <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension> tipo para o construtor de atributo.

5.  Adicionar o <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypeAttribute> à classe de atributo. Esse atributo especifica o identificador de cadeia de caracteres para o tipo de nó que você deseja estender.

     Para especificar os tipos de nó internas fornecidos pelo Visual Studio, passe um dos seguintes valores de enumeração para o construtor de atributo:

    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.ExplorerNodeTypes>: Use esses valores para especificar nós de conexão de site (os nós que exibem as URLs de site), de nós, ou todos os outros nós pai no site **Gerenciador de servidores**.

    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.Extensions.ExtensionNodeTypes>: Use esses valores para especificar um de nós internos que representam um componente individual em um site do SharePoint, como um nó que representa uma lista, campo ou tipo de conteúdo.

6.  Em sua implementação do <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeTypeExtension.Initialize%2A> método, use os membros de *nodeType* parâmetro para adicionar recursos para o nó. Esse parâmetro é um <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeType> objeto que fornece acesso para os eventos definidos na <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents> interface. Por exemplo, você pode manipular os eventos a seguir:

    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeChildrenRequested>: Manipule este evento para adicionar novos nós filhos para o nó. Para obter mais informações, confira [Como: Adicionar um nó do SharePoint personalizado ao Gerenciador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md).

    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodeMenuItemsRequested>: Manipule este evento para adicionar um item de menu de atalho personalizado para o nó.

    -   <xref:Microsoft.VisualStudio.SharePoint.Explorer.IExplorerNodeEvents.NodePropertiesRequested>: Manipule este evento para adicionar propriedades personalizadas para o nó. As propriedades aparecem na **propriedades** janela quando o nó é selecionado.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir demonstra como criar dois tipos diferentes de extensões de nó:

- Uma extensão que adiciona um item de menu de contexto para nós de site do SharePoint. Quando você clica no item de menu, ele exibe o nome do nó que foi clicado.

- Uma extensão que adiciona uma propriedade personalizada denominada **ContosoExampleProperty** para cada nó que representa um campo chamado **corpo**.

  [!code-csharp[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/serverexplorerextension.cs#9)]
  [!code-vb[SPExtensibility.ProjectSystemExtension.General#9](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/serverexplorerextension.vb#9)]

  Essa extensão adiciona uma propriedade de cadeia de caracteres editáveis para nós. Você também pode criar propriedades personalizadas que exibem dados somente leitura do servidor do SharePoint. Para obter um exemplo que demonstra como fazer isso, consulte [passo a passo: Estender o Gerenciador de servidores para exibir web parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer referências aos assemblies a seguir:

-   Microsoft.VisualStudio.SharePoint

-   Microsoft.VisualStudio.SharePoint.Explorer.Extensions

-   System.ComponentModel.Composition

-   System.Windows.Forms

## <a name="deploy-the-extension"></a>Implantar a extensão
 Para implantar o **Gerenciador de servidores** extensão, crie um [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você deseja distribuir com a extensão. Para obter mais informações, consulte [implantar extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte também
- [Como: Adicionar um nó do SharePoint personalizado ao Gerenciador de servidores](../sharepoint/how-to-add-a-custom-sharepoint-node-to-server-explorer.md)
- [Estender o nó de conexões do SharePoint no Gerenciador de servidores](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [Passo a passo: Estender o Gerenciador de servidores para exibir web parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)
- [Associar dados personalizados a extensões de ferramentas do SharePoint](../sharepoint/associating-custom-data-with-sharepoint-tools-extensions.md)
