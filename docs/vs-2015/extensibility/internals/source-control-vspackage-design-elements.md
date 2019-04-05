---
title: Elementos de Design de VSPackage do controle de origem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06cd4523f91c341029140764b31fbd0ee262d551
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926581"
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de design do VSPackage de controle do código-fonte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os tópicos nesta seção descrevem a estrutura de controle de fonte de VSPackage deve implementar para integração profunda. Também lista as interfaces e os serviços que o controle de fonte VSPackage podem implementar e as interfaces e os serviços de VSPackage do controle de origem pode usar de outros [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] componentes para dar suporte à sua fonte de modelo e a funcionalidade de controle.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Estrutura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)  
 Define a estrutura de VSPackage do controle de origem.  
  
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)  
 Lista de serviços e interfaces relacionadas ao pacote de controle de origem.  
  
 [Serviços fornecidos](../../extensibility/internals/services-provided-source-control-vspackage.md)  
 Descreve o serviço de controle do código-fonte fornecido pelo controle de fonte de VSPackage.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Discute como criar um controle de fonte VSPackage que não apenas fornece a funcionalidade de controle do código-fonte, mas pode ser usado para personalizar o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] da interface do usuário do controle de origem.
