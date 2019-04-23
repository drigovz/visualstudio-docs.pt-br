---
title: Estendendo o SharePoint empacotamento e implantação | Microsoft Docs
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
ms.openlocfilehash: 4bb98e2b1c83ff06570a77dc84ce6a7bf690f81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096992"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Estender o SharePoint empacotamento e implantação
  Você pode estender o empacotamento e o processo de implantação para projetos do SharePoint.

## <a name="create-deployment-steps"></a>Criar etapas de implantação
 Quando você implanta um projeto do SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] executa uma série de etapas de implantação. O Visual Studio inclui as etapas de implantação interna para muitas tarefas, como a retração e a adição de soluções. No entanto, você também pode criar suas próprias etapas de implantação.

 Para um passo a passo que demonstra como criar uma etapa de implantação, consulte [passo a passo: Criar uma etapa de implantação para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Criar configurações de implantação
 Uma configuração de implantação é um conjunto de etapas de implantação que é executado para um determinado projeto, mas pode afetar todos os itens de projeto do SharePoint. Todas as configurações de implantação inclui um conjunto de etapas que é executado quando o projeto é implantado e outro conjunto que é executado quando o projeto é retraído. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] inclui duas configurações de implantação interna, mas você também pode criar seus próprios. Quando você cria uma configuração de implantação, você pode incluir etapas de implantação interna e as etapas de implantação que você criar.

 Para um passo a passo que demonstra como criar uma configuração de implantação, consulte [passo a passo: Criar uma etapa de implantação para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Executar o código quando uma solução do SharePoint é implantada ou cancelada
 Você pode manipular eventos para executar tarefas adicionais quando uma solução do SharePoint é implantada ou cancelada. Visual Studio gera eventos que você pode manipular nos seguintes cenários:

- Antes e após a implantação de cada etapa é executada para um item de projeto do SharePoint. Para obter mais informações, confira [Como: Executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Antes e depois de um projeto do SharePoint é implantado ou cancelado. Para obter mais informações, confira [Como: Executar o código quando um projeto do SharePoint é implantado ou cancelado](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Lidar com conflitos de implantação
 Alguns tipos de itens de projeto do SharePoint, incluindo módulos, partes da Web, instâncias de lista e tipos de conteúdo, fornecem resolução de conflitos de implantação interna. Quando você implanta uma solução que contenha um desses itens de projeto, o Visual Studio primeiro verifica se um arquivo já existe no site do SharePoint com o mesmo nome, URL ou ID como um arquivo no item que você está implantando. Se houver um conflito, Visual Studio automaticamente pode resolver o conflito, ou você poderá ser solicitado para determinar se você deseja resolver o conflito ou cancelar a implantação tiver o Visual Studio. Para obter mais informações, consulte [implantação e solução de problemas de empacotamento de SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Você pode estender esse recurso, fornecendo seu próprio código que verifica e resolve conflitos de implantação. Para obter mais informações, confira [Como: Lidar com conflitos de implantação](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Executar operações de linha de comando antes ou depois que um projeto é implantado
 Se você quiser executar uma operação de linha de comando quando uma solução do SharePoint é implantada, você pode definir as <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> e <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> propriedades de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. Visual Studio executa esses comandos antes e depois que o projeto é implantado.

 Em alguns casos, você poderá ver os conflitos de implantação. Há várias maneiras diferentes para resolver conflitos. Para obter mais informações, consulte [SharePoint solucionar problemas de empacotamento e implantação](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Personalizar regras de validação
 Antes de implantar um pacote de solução (. wsp), você pode criar a funcionalidade personalizada e pacote regras de validação para verificar se o recurso ou o pacote é válido. Por exemplo, você pode relatar erros, avisos ou informações para desenvolvedores para ajudá-los a corrigir problemas de validação. Para obter mais informações, confira [Como: Criar recurso personalizado e um pacote de regras de validação para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Consulte também
- [Como: Executar código quando etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Passo a passo: Criar uma etapa de implantação para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Como: Criar pacote e um recurso personalizado de regras de validação para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
