---
title: Serviços fornecidos (controle do código-fonte VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, source control packages
- source control packages, services
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 13be907eeb35a2d4382fb63726c09cb2924e57e7
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723864"
---
# <a name="services-provided-source-control-vspackage"></a>Serviços fornecidos (VSPackage de controle do código-fonte)
Os serviços são o mecanismo principal por meio do qual a funcionalidade é compartilhada entre VSPackages e entre o IDE (ambiente de desenvolvimento integrado) do Visual Studio e seu VSPackages instalado. Para obter uma descrição detalhada dos serviços e sua importância no IDE do Visual Studio, consulte[usando e fornecendo serviços](../../extensibility/using-and-providing-services.md).

## <a name="the-source-control-service"></a>O serviço de controle do código-fonte
 O Visual Studio fornece duas camadas de serviços, serviços de nível IDE e serviços de nível de pacote. O IDE do Visual Studio fornece nativamente serviços de nível IDE. O pacote de controle do código-fonte consome alguns desses serviços. O pacote de controle do código-fonte como um VSPackage compartilha sua funcionalidade de controle do código-fonte fornecendo um serviço de controle do código-fonte privado próprio. O pacote de controle do código-fonte encapsula o conjunto de interfaces relacionadas ao controle do código-fonte implementado por ele na forma de um contrato que pode ser usado pelo IDE do Visual Studio.

## <a name="see-also"></a>Consulte também
- [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)