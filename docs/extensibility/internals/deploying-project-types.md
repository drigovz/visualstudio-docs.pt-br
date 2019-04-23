---
title: Implantar tipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e89f74d940182cd92fd15f726676f0979d21186
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60047209"
---
# <a name="deploy-project-types"></a>Implantar tipos de projeto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala um novo agregador do tipo de projeto (*ProjectAggregator2.dll*) e também um pacote do Windows Installer para redistribuição (*ProjectAggregator2.msi*). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona com limitações no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impede que os tipos de projeto de código gerenciado de funcionar corretamente. As etapas a seguir descrevem como alterar o VSPackage para usar o novo agregador.

1. Remova o projeto de NativeHierarchyWrapper da sua solução.

2. Remova os binários do NativeHierarchyWrapper de sua configuração.

3. Adicione *ProjectAggregator2.msi* à sua instalação.