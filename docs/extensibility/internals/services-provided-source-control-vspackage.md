---
title: Serviços fornecidos (Source Control VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f08ebe49756b442ef474ac2a032a72894f6bec15
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705401"
---
# <a name="services-provided-source-control-vspackage"></a>Serviços fornecidos (VSPackage de controle do código-fonte)
Os serviços são o principal mecanismo através do qual a funcionalidade é compartilhada entre vsPackages e entre o ambiente de desenvolvimento integrado (IDE) do Visual Studio e seus VSPackages instalados. Para obter uma descrição detalhada dos serviços e sua importância no Visual Studio IDE, consulte[Usando e Fornecendo Serviços](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>O Serviço de Controle de Origem
 O Visual Studio fornece duas camadas de serviços, serviços de nível IDE e serviços de nível de pacote. O Visual Studio IDE fornece nativamente serviços de nível IDE. O pacote de controle de origem consome alguns desses serviços. O pacote de controle de origem como um VSPackage compartilha sua funcionalidade de controle de origem, fornecendo um serviço de controle de origem privado próprio. O pacote de controle de origem encapsula o conjunto de interfaces relacionadas ao controle de fonte implementadas por ele na forma de um contrato que pode ser usado pelo Visual Studio IDE.

## <a name="see-also"></a>Confira também
- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)
