---
title: 'Como: Definir comandos de implantação do SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, deploying
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e76a1e4e19f8f3280b6da71dffa19d3a7e2c16a5
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54871768"
---
# <a name="how-to-set-sharepoint-deployment-commands"></a>Como: Definir comandos de implantação do SharePoint
  Você pode personalizar o processo de implantação, definindo comandos pré e pós-implantação. Esses comandos são executados antes e depois de outras ações de implantação quando você depura soluções do SharePoint no Visual Studio.  
  
### <a name="to-add-a-pre-deployment-command"></a>Para adicionar um comando de pré-implantação  
  
1.  Na barra de menus, escolha **Project** > **\<*ProjectName*> propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pré-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório antes da conclusão da implantação, insira **dir**.  
  
### <a name="to-add-a-post-deployment-command"></a>Para adicionar um comando de pós-implantação  
  
1.  Na barra de menus, escolha **Project** > **\<*ProjectName*> propriedades**.  
  
2.  Escolha o **SharePoint** guia.  
  
3.  No **linha de comando de pós-implantação** texto, digite os comandos do MS-DOS ou MSBuild para personalizar esta etapa.  
  
     Por exemplo, para listar o conteúdo do diretório após a conclusão da implantação, insira **dir**. Para usar uma variável do MSBuild para copiar o assembly do diretório de compilação, digite **copiar $ (TargetPath) c:\DeploymentDirectory**.  
  
## <a name="see-also"></a>Consulte também
 [Empacotar e implantar soluções do SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
