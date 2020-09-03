---
title: Implantando tipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708785"
---
# <a name="deploy-project-types"></a>Implantar tipos de projeto
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] instala um novo agregador de tipo de projeto (*ProjectAggregator2.dll*) e também um pacote Windows Installer para redistribuição (*ProjectAggregator2.msi*). Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 trabalha em relação às limitações no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] agregador de projeto que impede que os tipos de projeto de código gerenciado funcionem corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.

1. Remova o projeto NativeHierarchyWrapper da sua solução.

2. Remova todos os binários do NativeHierarchyWrapper da sua configuração.

3. Adicione *ProjectAggregator2.msi* à sua instalação.
