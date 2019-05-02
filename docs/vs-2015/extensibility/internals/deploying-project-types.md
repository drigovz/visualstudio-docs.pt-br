---
title: Implantar tipos de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0fda84d5f7467a65b254d3b12b0466b6ab415d61
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076466"
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instala um novo agregador do tipo de projeto (ProjectAggregator2.dll) e também um pacote do Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona alternativas limitações no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projeto agregador que impedem a tipos de projeto de código gerenciado de funcionar corretamente. As etapas a seguir descrevem como alterar o VSPackage para usar o novo agregador.  
  
1. Remova o projeto de NativeHierarchyWrapper da sua solução.  
  
2. Remova os binários do NativeHierarchyWrapper de sua configuração.  
  
3. Adicione ProjectAggregator2.msi à sua instalação.
