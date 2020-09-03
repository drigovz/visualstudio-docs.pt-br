---
title: Implantando tipos de projeto | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196875"
---
# <a name="deploying-project-types"></a>Tipos de projeto de implantação
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] instala um novo agregador de tipo de projeto (ProjectAggregator2.dll) e também um pacote Windows Installer para redistribuição (ProjectAggregator2.msi). Você deve usar o novo agregador para tipos de projeto de código gerenciado. O ProjectAggregator2 funciona em volta das limitações no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] agregador de projeto que impede que os tipos de projeto de código gerenciado funcionem corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.  
  
1. Remova o projeto NativeHierarchyWrapper da sua solução.  
  
2. Remova todos os binários do NativeHierarchyWrapper da sua configuração.  
  
3. Adicione ProjectAggregator2.msi à sua instalação.
