---
title: Seleção e hierarquias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 741d61f4f3a62638e56aabb1f62f97aac4519d0c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596575"
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