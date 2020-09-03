---
title: Arquitetura de tipos de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], architecture
ms.assetid: 9c1d940f-8a54-41f7-a8aa-c870e324371c
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 775656d2190a36f62c2b047c1ff7f1e02575c1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68154151"
---
# <a name="project-types-architecture"></a>Arquitetura de tipos de projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Esta seção contém informações detalhadas sobre a arquitetura dos tipos de projeto no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)  
 Lista os serviços que um tipo de projeto pode consumir e as interfaces que ele deve implementar.  
  
 [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)  
 Descreve as interfaces que os tipos de projeto devem implementar e, opcionalmente, podem implementar para fornecer funcionalidade adicional.  
  
 [Quando criar tipos de projeto](../../extensibility/internals/when-to-create-project-types.md)  
 Ajuda a decidir quando você deve criar um tipo de projeto e quando você pode usar outro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] recurso de extensibilidade, como VSPackages e editores para atingir o mesmo objetivo.  
  
 [Hierarquias e seleção](../../extensibility/internals/hierarchies-and-selection.md)  
 Descreve como o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] usa hierarquias e contexto de seleção para fornecer uma experiência de usuário consistente e simplificada.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Subtipos de projeto](../../extensibility/internals/project-subtypes.md)  
 Explica como os subtipos de projeto permitem personalizar o comportamento dos sistemas de projeto do [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e do [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] .  
  
 [Tipos de Projeto](../../extensibility/internals/project-types.md)  
 Fornece uma visão geral dos projetos como os blocos de construção básicos do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (ambiente de desenvolvimento integrado). São fornecidos links para tópicos adicionais que explicam como os projetos controlam a criação e a compilação de código.
