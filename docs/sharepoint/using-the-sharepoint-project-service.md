---
title: Usando o serviço de projeto do SharePoint | Microsoft Docs
description: Use o serviço de projeto do SharePoint para executar tarefas relacionadas ao sistema de projeto. Exiba uma lista de recursos de serviço do projeto.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint project service
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5366be3ed60da9225eaf10b19f58ccd77bffbb90
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99892184"
---
# <a name="use-the-sharepoint-project-service"></a>Usar o serviço de projeto do SharePoint
  O sistema de projeto do SharePoint inclui um serviço de projeto que você pode usar para executar tarefas relacionadas ao sistema de projeto. O serviço de projeto é um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto.

 Você pode acessar o serviço de projeto do SharePoint em qualquer extensão de ferramentas do SharePoint. Você também pode acessá-lo em outros tipos de extensões do Visual Studio, como add-ins e VSPackages. Para obter mais informações, consulte [como recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).

## <a name="project-service-features"></a>Recursos do serviço de projeto
 A tabela a seguir lista as tarefas que você pode executar usando o serviço de projeto do SharePoint e o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> método ou a propriedade a ser usada para executar cada tarefa.

|Tarefa|Membro a ser usado|
|----------|-------------------|
|Acesse qualquer projeto do SharePoint que esteja aberto no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|
|Acesse todos os tipos de item de projeto do SharePoint disponíveis (incluindo tipos de item de projeto internos e personalizados).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|
|Acesse todas as etapas de implantação disponíveis para projetos do SharePoint (incluindo etapas de implantação internas e personalizadas).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|
|Acessar eventos que são gerados quando um desenvolvedor refatorar o código em um projeto do SharePoint.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|
|Execute um *comando personalizado do SharePoint* que chama o modelo de objeto do SharePoint Server. Para obter mais informações sobre os comandos do SharePoint, consulte [chamar para os modelos de objeto do SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|
|Converter um tipo no sistema de projeto do SharePoint para um tipo no modelo de objeto de automação do Visual Studio ou no modelo de objeto de integração e vice-versa. Para obter mais informações, consulte [converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|
|Grave mensagens na janela de **saída** ou na janela de **lista de erros** no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|
|Acesse outros serviços que estão disponíveis no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|
|Recupere o caminho para a pasta de instalação do site do SharePoint local que é usado para depurar a solução.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|
|Determine se [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] o ou o está instalado no computador.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|
|Validar um recurso ou pacote em uma solução do SharePoint.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|

## <a name="see-also"></a>Confira também
- [Converter entre os tipos do sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Como recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)
- [Estenda as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [Visão geral do modelo de programação das extensões de ferramentas do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Como obter um serviço do objeto DTE](/previous-versions/bb166401(v=vs.140))