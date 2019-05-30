---
title: Seleção e hierarquias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3d59a5160b5c20a3243426eaf1fda4b72e58e93
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328875"
---
# <a name="hierarchies-and-selection"></a>Seleção e hierarquias
Quando você personaliza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], você deve compreender como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lida com hierarquias como projetos e como ele usa o contexto de seleção para determinar o que é exibido ao usuário. Esta seção aborda os conceitos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seleção e hierarquias.

## <a name="in-this-section"></a>Nesta seção
- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Descreve o conceito geral de hierarquias e hierarquias de projeto.

- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Descreve como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE) mantém informações sobre os objetos do usuário ativo no momento e permite que os VSPackages acompanhar moeda.

- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)

 Discute o modelo de como você pode determinar o foco de contexto de seleção do usuário em uma janela.

- [Comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md)

 Discute como a funcionalidade disponível em [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] baseia-se no contexto da seleção atual do usuário e o contexto geral do IDE.

## <a name="related-sections"></a>Seções relacionadas
- [Arquitetura de tipos de projeto](../../extensibility/internals/project-types-architecture.md)

 Fornece informações técnicas detalhadas sobre tipos de projeto.