---
title: 'Converta: Tipos de sistema de projeto do SharePoint para/de outros tipos'
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
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835991"
---
# <a name="convert-between-sharepoint-project-system-types-and-other-visual-studio-project-types"></a>Converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio
  Em alguns casos, você pode ter um objeto no sistema de projeto do SharePoint e você deseja usar recursos de um objeto correspondente no modelo de objeto de automação do Visual Studio ou modelo de objeto de integração, ou vice-versa. Nesses casos, você pode usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método do serviço de projeto do SharePoint para converter o objeto para um modelo de objeto diferente.

 Por exemplo, você pode ter um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto, mas você deseja usar métodos que estão disponíveis somente em um <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> objeto. Nesse caso, você pode usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para converter os <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> para um <xref:EnvDTE.Project> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>.

 Para obter mais informações sobre o modelo de objeto de automação do Visual Studio e o modelo de objeto de integração do Visual Studio, consulte [extensões de ferramentas de visão geral do modelo de programação do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="types-of-conversions"></a>Tipos de conversões
 A tabela a seguir lista os tipos que esse método pode converter entre o sistema de projeto do SharePoint e os outros modelos de objeto do Visual Studio.

|Tipo de sistema de projeto do SharePoint|Tipos correspondentes nos modelos de objeto de integração e automação|
|------------------------------------|-------------------------------------------------------------------------|
|<xref:Microsoft.VisualStudio.SharePoint.ISharePointProject>|<xref:EnvDTE.Project><br /><br /> ou<br /><br /> Qualquer interface em que o modelo de objeto de integração do Visual Studio que é implementado por objeto para o projeto COM base. Essas interfaces incluem <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>, <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject> (ou uma interface derivada), e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage>. Para obter uma lista das principais interfaces que são implementadas por projetos, consulte [componentes principais do projeto modelo](../extensibility/internals/project-model-core-components.md).|
|<xref:Microsoft.VisualStudio.SharePoint.IMappedFolder><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItem><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectItemFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeature><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectFeatureResourceFile><br /><br /> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectPackage>|<xref:EnvDTE.ProjectItem><br /><br /> ou<br /><br /> Um<xref:System.UInt32> valor (também chamado de um VSITEMID) que identifica o membro de projeto na <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> que o contém. Esse valor pode ser passado para o *itemid* parâmetro de alguns <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> métodos.|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir demonstra como usar o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A> método para converter um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> do objeto para um <xref:EnvDTE.Project>.

 [!code-csharp[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/CSharp/spprojectserviceaddin/connect.cs#2)]
 [!code-vb[SPExtensibility.ProjectService.FromDTE#2](../sharepoint/codesnippet/VisualBasic/spprojectserviceaddin/connect.vb#2)]

 Este exemplo requer:

- Uma extensão do sistema de projeto do SharePoint que tem uma referência para o *EnvDTE.dll* assembly. Para obter mais informações, consulte [estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md).

- Código que registra o `projectService_ProjectAdded` método para lidar com o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.ProjectAdded> eventos de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obter um exemplo, consulte [ Criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md).

## <a name="see-also"></a>Consulte também

- [Usar o serviço de projeto do SharePoint](../sharepoint/using-the-sharepoint-project-service.md)
- [Como: Recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Extensões de ferramentas de visão geral do modelo de programação do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
