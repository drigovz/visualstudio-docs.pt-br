---
title: Elementos de Design de VSPackage do controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f4446bb0cab421e06910ac7f7c5893680c36edf6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872222"
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de design do VSPackage de controle do código-fonte
Os tópicos nesta seção descrevem a estrutura de controle de fonte de VSPackage deve implementar para integração profunda. Também lista as interfaces e os serviços que o controle de fonte VSPackage podem implementar e as interfaces e os serviços de VSPackage do controle de origem pode usar de outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes para dar suporte à sua fonte de modelo e a funcionalidade de controle.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Define a estrutura de VSPackage do controle de origem.  
  
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Lista de serviços e interfaces relacionadas ao pacote de controle de origem.  
  
 [Serviços fornecidos](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descreve o serviço de controle do código-fonte fornecido pelo controle de fonte de VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de fonte VSPackage que não apenas fornece a funcionalidade de controle do código-fonte, mas pode ser usado para personalizar o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] da interface do usuário do controle de origem.