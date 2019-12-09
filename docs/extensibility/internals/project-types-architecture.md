---
title: Arquitetura de tipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6d77524097509c45c23d6a3d9cc147e5aba6691d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318895"
---
# <a name="project-types-architecture"></a>Arquitetura de tipos de projeto
Esta seção contém informações detalhadas sobre a arquitetura de tipos de projeto no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="in-this-section"></a>Nesta seção
- [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)

 Lista os serviços de que um tipo de projeto pode consumir e as interfaces que ele deve implementar.

- [Componentes principais do modelo de projeto](../../extensibility/internals/project-model-core-components.md)

 Descreve as interfaces para tipos de projeto devem implementar e, opcionalmente, podem ser implementados para fornecer funcionalidade adicional.

- [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)

 Digite ajuda você a decidir quando você deve criar um projeto e quando você usa outro [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] recurso de extensibilidade, como os VSPackages e editores para alcançar o mesmo objetivo.

- [Seleção e hierarquias](../../extensibility/internals/hierarchies-and-selection.md)

 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa o contexto de seleção e hierarquias para fornecer uma experiência de usuário consistente e simplificada.

## <a name="related-sections"></a>Seções relacionadas
- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)

 Explica como os subtipos do projeto permitem que você personalize o comportamento dos sistemas de projeto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)].

- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece uma visão geral dos projetos como blocos de construção básicos do [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o ambiente de desenvolvimento integrado (IDE). São fornecidos links para tópicos adicionais que explicam como projetos de controle de criação e compilação de código.