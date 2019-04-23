---
title: 'Como: Código de execução quando um projeto do SharePoint é implantado ou retraído | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4aadc089fba5c1f55488c72bfd5c3e46ebf59487
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60084395"
---
# <a name="how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Como: Executar o código quando um projeto do SharePoint é implantado ou cancelado
  Se você quiser realizar tarefas adicionais quando um projeto do SharePoint é implantado ou cancelado, você pode manipular eventos que são gerados pelo Visual Studio. Para obter mais informações, consulte [estender o SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

### <a name="to-run-code-when-a-sharepoint-project-is-deployed-or-retracted"></a>Para executar código quando um projeto do SharePoint é implantado ou cancelado

1. Crie uma extensão de item de projeto, uma extensão de projeto ou uma definição de um novo tipo de item de projeto. Para mais informações, consulte os seguintes tópicos:

   - [Como: Criar uma extensão de item de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-item-extension.md)

   - [Como: Criar uma extensão de projeto do SharePoint](../sharepoint/how-to-create-a-sharepoint-project-extension.md)

   - [Como: Definir um tipo de item de projeto do SharePoint](../sharepoint/how-to-define-a-sharepoint-project-item-type.md)

2. Na extensão, acesse o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto. Para obter mais informações, confira [Como: Recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

3. Lidar com o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos do serviço de projeto.

4. No evento manipuladores, use o <xref:Microsoft.VisualStudio.SharePoint.DeploymentEventArgs> para obter informações sobre a sessão atual de implantação. Por exemplo, você pode determinar qual projeto é na sessão atual de implantação e se ele está sendo implantado ou cancelado.

   O exemplo de código a seguir demonstra como lidar com o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentStarted> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectEvents.DeploymentCompleted> eventos em uma extensão de projeto. Essa extensão grava uma mensagem adicional para o **saída** janela quando a implantação é iniciada e concluída para um projeto do SharePoint.

   [!code-csharp[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/CSharp/projectsystemexamples/extension/handleprojectdeploymentevents.cs#12)]
   [!code-vb[SPExtensibility.ProjectSystemExtension.General#12](../sharepoint/codesnippet/VisualBasic/projectsystemexamples/extension/handleprojectdeploymentevents.vb#12)]

## <a name="compile-the-code"></a>Compilar o código
 Este exemplo requer referências aos assemblies a seguir:

- Microsoft.VisualStudio.SharePoint

- System.ComponentModel.Composition

## <a name="deploy-the-extension"></a>Implantar a extensão
 Para implantar a extensão, crie um [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] pacote de extensão (VSIX) para o assembly e outros arquivos que você deseja distribuir com a extensão. Para obter mais informações, consulte [implantar extensões para ferramentas do SharePoint no Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Consulte também
- [Estender o SharePoint empacotamento e implantação](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [Como: Executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
