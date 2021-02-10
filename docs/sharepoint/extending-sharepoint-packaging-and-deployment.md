---
title: Estendendo a implantação e empacotamento do SharePoint | Microsoft Docs
description: Estenda o empacotamento e a implantação do SharePoint. Criar etapas e configurações de implantação. Lidar com conflitos de implantação. Personalizar regras de validação.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending deployment
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd4967e38738018f9b30365575a2dcb9e8970963
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948746"
---
# <a name="extend-sharepoint-packaging-and-deployment"></a>Estender o empacotamento e a implantação do SharePoint
  Você pode estender o processo de empacotamento e implantação para projetos do SharePoint.

## <a name="create-deployment-steps"></a>Criar etapas de implantação
 Quando você implanta um projeto do SharePoint, [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] o executa uma série de etapas de implantação. O Visual Studio inclui etapas de implantação internas para muitas tarefas, como o cancelamento e a adição de soluções. No entanto, você também pode criar suas próprias etapas de implantação.

 Para obter instruções que demonstram como criar uma etapa de implantação, consulte [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="create-deployment-configurations"></a>Criar configurações de implantação
 Uma configuração de implantação é um conjunto de etapas de implantação que é executado para um determinado projeto, mas pode afetar todos os itens de projeto do SharePoint. Cada configuração de implantação inclui um conjunto de etapas que é executado quando o projeto é implantado e outro conjunto que é executado quando o projeto é cancelado. [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] inclui duas configurações de implantação internas, mas você também pode criar as suas próprias. Ao criar uma configuração de implantação, você pode incluir etapas de implantação internas e etapas de implantação que você criar.

 Para obter instruções que demonstram como criar uma configuração de implantação, consulte [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md).

## <a name="run-code-when-a-sharepoint-solution-is-deployed-or-retracted"></a>Executar código quando uma solução do SharePoint é implantada ou recolhida
 Você pode manipular eventos para executar tarefas adicionais quando uma solução do SharePoint é implantada ou cancelada. O Visual Studio gera eventos que você pode manipular nos seguintes cenários:

- Antes e depois de cada etapa de implantação ser executada para um item de projeto do SharePoint. Para obter mais informações, consulte [como: executar código quando as etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md).

- Antes e depois de um projeto do SharePoint ser implantado ou cancelado. Para obter mais informações, consulte [como: executar código quando um projeto do SharePoint é implantado ou cancelado](../sharepoint/how-to-run-code-when-a-sharepoint-project-is-deployed-or-retracted.md).

## <a name="handle-deployment-conflicts"></a>Lidar com conflitos de implantação
 Alguns tipos de itens de projeto do SharePoint, incluindo módulos, Web Parts, instâncias de lista e tipos de conteúdo, fornecem resolução de conflitos de implantação interna. Quando você implanta uma solução que contém um desses itens de projeto, o Visual Studio verifica primeiro se um arquivo já existe no site do SharePoint com o mesmo nome, URL ou ID que um arquivo no item que você está implantando. Se houver um conflito, o Visual Studio poderá resolver automaticamente o conflito ou poderá solicitar que você determine se deseja que o Visual Studio resolva o conflito ou cancele a implantação. Para obter mais informações, consulte [solução de problemas de empacotamento e implantação do SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

 Você pode estender esse recurso fornecendo seu próprio código que verifica e resolve conflitos de implantação. Para obter mais informações, consulte [como tratar conflitos de implantação](../sharepoint/how-to-handle-deployment-conflicts.md).

## <a name="run-command-line-operations-before-or-after-a-project-is-deployed"></a>Executar operações de linha de comando antes ou depois de um projeto ser implantado
 Se você quiser executar uma operação de linha de comando quando uma solução do SharePoint for implantada, poderá definir as <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PreDeploymentCommand%2A> <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject.PostDeploymentCommand%2A> Propriedades e de um <xref:Microsoft.VisualStudio.SharePoint.ISharePointProject> objeto. O Visual Studio executa esses comandos antes e depois que o projeto é implantado.

 Em alguns casos, você poderá ver conflitos de implantação. Há várias maneiras diferentes de resolver conflitos. Para obter mais informações, consulte [solução de problemas de empacotamento e implantação do SharePoint](../sharepoint/troubleshooting-sharepoint-packaging-and-deployment.md).

## <a name="customize-validation-rules"></a>Personalizar regras de validação
 Antes de implantar um pacote de solução (. wsp), você pode criar regras de validação de pacotes e recursos personalizados para verificar se o recurso ou pacote é válido. Por exemplo, você pode relatar informações, avisos ou erros aos desenvolvedores para ajudá-los a corrigir problemas de validação. Para obter mais informações, consulte [como criar regras personalizadas de validação de pacotes e recursos para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).

## <a name="see-also"></a>Consulte também
- [Como executar código quando as etapas de implantação são executadas](../sharepoint/how-to-run-code-when-deployment-steps-are-executed.md)
- [Walkthrough: criar uma etapa de implantação personalizada para projetos do SharePoint](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)
- [Como criar regras de validação de pacotes e recursos personalizados para soluções do SharePoint](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md)
- [Estender o sistema de projeto do SharePoint](../sharepoint/extending-the-sharepoint-project-system.md)
