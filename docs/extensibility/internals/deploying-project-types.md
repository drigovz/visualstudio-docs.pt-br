---
title: Implantando tipos de projetos | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708785"
---
# <a name="deploy-project-types"></a>Implantar tipos de projetos
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]instala um novo agregador do tipo projeto *(ProjectAggregator2.dll)* e também um pacote do Windows Installer para redistribuição *(ProjectAggregator2.msi).* Você deve usar o novo agregador para tipos de projeto de código gerenciado. ProjectAggregator2 trabalha em torno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de limitações no agregador de projetos que impede que tipos de projeto de código gerenciado funcionem corretamente. As etapas a seguir descrevem como alterar seu VSPackage para usar o novo agregador.

1. Remova o projeto NativeHierarchyWrapper da sua solução.

2. Remova quaisquer binários NativeHierarchyWrapper da sua configuração.

3. Adicione *ProjectAggregator2.msi* à sua configuração.
