---
title: Hierarquias e seleção | Microsoft Docs
description: Saiba como o Visual Studio lida com hierarquias, como projetos, e como ele usa o contexto de seleção para determinar o que é exibido para o usuário.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, hierarchies
- selection
- hierarchies
ms.assetid: cad0a859-7a84-4ce5-b0a9-f7f64e5f8ebb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 04f433e3da45e10d2b1721ac13254856489d2d0a
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96480415"
---
# <a name="hierarchies-and-selection"></a>Hierarquias e seleção
Ao personalizar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o, você deve entender como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lida com hierarquias como projetos e como ele usa o contexto de seleção para determinar o que é exibido para o usuário. Esta seção aborda os conceitos de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] hierarquias e seleção.

## <a name="in-this-section"></a>Nesta seção
- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)

 Descreve as hierarquias de projeto e o conceito geral de hierarquias.

- [Seleção e moeda no IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)

 Descreve como o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) mantém informações sobre os objetos ativos do usuário atualmente e permite que o VSPackages acompanhe a moeda.

- [Objetos de contexto de seleção](../../extensibility/internals/selection-context-objects.md)

 Discute o modelo de como você pode determinar o foco de contexto de seleção do usuário em uma janela.

- [Comentários para o usuário](../../extensibility/internals/feedback-to-the-user.md)

 Discute como a funcionalidade disponível no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] é baseada no contexto de seleção atual do usuário e no contexto geral do IDE.

## <a name="related-sections"></a>Seções relacionadas
- [Arquitetura de tipos de projeto](../../extensibility/internals/project-types-architecture.md)

 Fornece informações técnicas detalhadas sobre os tipos de projeto.
