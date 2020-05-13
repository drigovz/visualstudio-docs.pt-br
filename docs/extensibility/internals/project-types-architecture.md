---
title: Arquitetura de tipos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e53929b1ec2ed9c73191bf16f1cedc84a53b58f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706314"
---
# <a name="project-types-architecture"></a>Arquitetura de tipos de projeto
Esta seção contém informações detalhadas [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]sobre a arquitetura dos tipos de projeto em .

## <a name="in-this-section"></a>Nesta seção
- [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)

 Lista os serviços que um tipo de projeto pode consumir e as interfaces que ele deve implementar.

- [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)

 Descreve os tipos de projeto de interfaces que ambos devem implementar e, opcionalmente, podem implementar para fornecer funcionalidade adicional.

- [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)

 Ajuda você a decidir quando você deve criar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um tipo de projeto e quando você pode usar outro recurso de extensibilidade, como VSPackages e editores para alcançar o mesmo objetivo.

- [Hierarquias e seleção](../../extensibility/internals/hierarchies-and-selection.md)

 Descreve como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] usa hierarquias e contexto de seleção para fornecer uma experiência de usuário consistente e simplificada.

## <a name="related-sections"></a>Seções relacionadas
- [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)

 Explica como os subtipos do projeto permitem [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] personalizar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]o comportamento dos sistemas de projeto de e .

- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Fornece uma visão geral dos projetos como [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os blocos básicos de construção do ambiente de desenvolvimento integrado (IDE). Links são fornecidos para tópicos adicionais que explicam como os projetos controlam a construção e compilação de códigos.
