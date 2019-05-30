---
title: Implantar tipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac03682fa1158f5da9c694cf1be5282717c07b55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312171"
---
# <a name="deploy-project-types"></a>Implantar tipos de projeto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala um novo agregador do tipo de projeto (*ProjectAggregator2.dll*) e também um pacote do Windows Installer para redistribuição (*ProjectAggregator2.msi*). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 funciona com limitações no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto agregador que impede que os tipos de projeto de código gerenciado de funcionar corretamente. As etapas a seguir descrevem como alterar o VSPackage para usar o novo agregador.

1. Remova o projeto de NativeHierarchyWrapper da sua solução.

2. Remova os binários do NativeHierarchyWrapper de sua configuração.

3. Adicione *ProjectAggregator2.msi* à sua instalação.