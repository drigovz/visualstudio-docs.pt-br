---
title: 'Convert: tipos de sistema de projeto do SharePoint de/para outros tipos'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 40ea60a8df5bc0bcd033c60a83d742ed3249cc53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "66835991"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Converter entre os tipos do sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio
  Em alguns casos, você pode ter um objeto no sistema de projeto do SharePoint e deseja usar recursos de um objeto correspondente no modelo de objeto de automação ou no modelo de objeto de integração do Visual Studio ou vice-versa. Nesses casos, você pode usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método do serviço de projeto do SharePoint para converter o objeto em um modelo de objeto diferente.

 Por exemplo, você pode ter um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto, mas deseja usar métodos que estão disponíveis somente em um <xref:EnvDTE.Project> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objeto ou. Nesse caso, você pode usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para converter o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> para um <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> .

 Para obter mais informações sobre o modelo de objeto de automação do Visual Studio e o modelo de objeto de integração do Visual Studio, consulte [visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipos de conversões
 A tabela a seguir lista os tipos que esse método pode converter entre o sistema de projeto do SharePoint e os outros modelos de objeto do Visual Studio.

|Tipo de sistema de projeto do SharePoint|Tipos correspondentes nos modelos de objeto de automação e integração|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> ou<br /><br /> Qualquer interface no modelo de objeto de integração do Visual Studio que é implementada pelo objeto COM subjacente para o projeto. Essas interfaces incluem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> , <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (ou uma interface derivada) e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> . Para obter uma lista das principais interfaces implementadas por projetos, consulte [Project Model Core Components](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> ou<br /><br /> Um <xref:System.UInt32> valor (também chamado de VSITEMID) que identifica o membro do projeto no <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que o contém. Esse valor pode ser passado para o parâmetro *ItemId* de alguns <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos.|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir demonstra como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para converter um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto em um <xref:EnvDTE.Project> .

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Este exemplo requer:

- Uma extensão do sistema de projeto do SharePoint que tem uma referência ao assembly *EnvDTE.dll* . Para obter mais informações, consulte [estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- O código que registra o `projectService_ProjectAdded` método para manipular o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> evento de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obter um exemplo, consulte [como: criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Confira também

- [Usar o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Como recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
