---
title: Elementos de design vspackage de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control packages, design elements
ms.assetid: edd3f2ff-ca32-4465-8ace-4330493b67bb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5e94829f781c058d9b0ea56cdec6c03c71ffe0c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705003"
---
# <a name="source-control-vspackage-design-elements"></a>Elementos de design do VSPackage de controle do código-fonte
Os tópicos desta seção descrevem a estrutura que o controle de origem VSPackage deve implementar para uma integração profunda. Ele também lista as interfaces e serviços que o controle de origem VSPackage pode implementar, e as interfaces e serviços que o controle de origem VSPackage pode usar de outros [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] componentes para suportar seu modelo de controle de origem e funcionalidade.

## <a name="in-this-section"></a>Nesta seção
- [Estrutura de VSPackage](../../extensibility/internals/vspackage-structure-source-control-vspackage.md)

 Define a estrutura do controle de origem VSPackage.

- [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)

 Lista interfaces e serviços relacionados ao pacote de controle de origem.

- [Serviços fornecidos](../../extensibility/internals/services-provided-source-control-vspackage.md)

 Descreve o serviço de controle de origem fornecido pelo controle de origem VSPackage.

## <a name="related-sections"></a>Seções relacionadas
- [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)

 Discute como criar um controle de origem VSPackage que não apenas fornece a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] funcionalidade de controle de origem, mas pode ser usado para personalizar a ui de controle de origem.
