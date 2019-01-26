---
title: Usando o serviço de projeto do SharePoint | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 90df435e2c6c20b43d12169b32780eefc22c1d70
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871540"
---
# <a name="use-the-sharepoint-project-service"></a>Usar o serviço de projeto do SharePoint
  O sistema de projeto do SharePoint inclui um serviço de projeto que você pode usar para executar tarefas relacionadas ao sistema de projeto. O serviço de projeto é um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> objeto.  
  
 Você pode acessar o serviço de projeto do SharePoint em qualquer extensão de ferramentas do SharePoint. Você também pode acessá-lo em outros tipos de extensões do Visual Studio, como add-ins e VSPackages. Para obter mais informações, confira [Como: Recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md).  
  
## <a name="project-service-features"></a>Recursos do serviço de projeto
 A tabela a seguir lista as tarefas que você pode executar usando o serviço de projeto do SharePoint e o <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService> método ou propriedade a ser usada para executar cada tarefa.  
  
|Tarefa|Membro a ser usado|  
|----------|-------------------|  
|Acesse qualquer projeto do SharePoint que está aberto no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Projects%2A>.|  
|Acesse todos os tipos de item de projeto do SharePoint que estão disponíveis (incluindo tipos de item de projeto internos e personalizados).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ProjectItemTypes%2A>.|  
|Acesse todas as etapas de implantação que estão disponíveis para projetos do SharePoint (incluindo as etapas de implantação internas e personalizadas).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.DeploymentSteps%2A>.|  
|Eventos de acesso que são gerados quando um desenvolvedor refatora o código em um projeto do SharePoint.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.CodeRefactoringEvents%2A>.|  
|Executar um personalizado *comando do SharePoint* que chama o modelo de objeto de servidor do SharePoint. Para obter mais informações sobre comandos do SharePoint, consulte [chamam os modelos de objeto SharePoint](../sharepoint/calling-into-the-sharepoint-object-models.md).|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointConnection%2A>.|  
|Converter um tipo no sistema de projeto do SharePoint para um tipo no modelo de objeto de automação do Visual Studio ou modelo de objeto de integração e vice-versa. Para obter mais informações, consulte [converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).|Método <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Convert%2A>.|  
|Gravar mensagens para o **saída** janela ou **lista de erros** janela no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.Logger%2A>.|  
|Acesse outros serviços que estão disponíveis no Visual Studio.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.ServiceProvider%2A>.|  
|Recupere o caminho para a pasta de instalação do site do SharePoint local que é usado para depurar a solução.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.SharePointInstallPath%2A>.|  
|Determinar se [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ou [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] está instalado no computador.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.IsSharePointInstalled%2A>.|  
|Valide um recurso ou um pacote em uma solução do SharePoint.|Propriedade <xref:Microsoft.VisualStudio.SharePoint.ISharePointProjectService.PackageValidationProvider%2A>.|  
  
## <a name="see-also"></a>Consulte também
 [Converter entre tipos de sistema de projeto do SharePoint e outros tipos de projeto do Visual Studio](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)   
 [Como: Recuperar o serviço de projeto do SharePoint](../sharepoint/how-to-retrieve-the-sharepoint-project-service.md)   
 [Estender as ferramentas do SharePoint no Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Extensões de ferramentas de visão geral do modelo de programação do SharePoint](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Como: Obtenha um serviço do objeto DTE](https://msdn.microsoft.com/library/bb166401.aspx)  
