---
title: Como definir comandos de implantação do SharePoint | Microsoft Docs
description: Entenda como personalizar o processo de implantação definindo os comandos pré-implantação e pós-implantação do SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 72938f316be22cd9b2eab2d7dab893c9370fb0ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965844"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Como definir comandos de implantação do SharePoint
  Você pode personalizar o processo de implantação Configurando comandos pré-implantação e pós-implantação. Esses comandos são executados antes e depois de outras ações de implantação quando você depura soluções do SharePoint do Visual Studio.

### <a name="to-add-a-pre-deployment-command"></a>Para adicionar um comando de pré-implantação

1. Na barra de menus, escolha   >  **\<*ProjectName*> Propriedades** do projeto.

2. Escolha a guia **SharePoint** .

3. Na caixa de texto **linha de comando de pré-implantação** , digite comandos do MS-dos ou MSBuild para personalizar esta etapa.

     Por exemplo, para listar o conteúdo do diretório antes da conclusão da implantação, insira **dir**.

### <a name="to-add-a-post-deployment-command"></a>Para adicionar um comando pós-implantação

1. Na barra de menus, escolha   >  **\<*ProjectName*> Propriedades** do projeto.

2. Escolha a guia **SharePoint** .

3. Na caixa de texto de **linha de comando pós-implantação** , insira comandos MS-dos ou MSBuild para personalizar esta etapa.

     Por exemplo, para listar o conteúdo do diretório após a conclusão da implantação, insira **dir**. Para usar uma variável do MSBuild para copiar o assembly do diretório de compilação, digite **Copy $ (TargetPath) c:\DeploymentDirectory**.

## <a name="see-also"></a>Consulte também
- [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
