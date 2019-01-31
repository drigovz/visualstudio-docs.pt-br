---
title: Assemblies satélite de segurança e localizados | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b4c153697d95f1496ee3380f63c48d0e4521c05a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781015"
---
# <a name="security-and-localized-satellite-assemblies"></a>Assemblies satélite de segurança e localizados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se seu assembly principal usar nomenclatura forte, assemblies satélites deverão ser assinados com a mesma chave privada que o assembly principal. Se o par de chave pública/privada não corresponder entre os assemblies satélites e principal, seus recursos não serão carregados. Para obter mais informações sobre a assinatura de assemblies, veja [Como: Assinar um assembly com um nome forte](http://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).  
  
 Em geral, você poderá precisar que o grupo de assinatura da sua organização ou uma organização de assinatura externa assine com a chave privada. Isso ocorre devido à natureza confidencial da chave privada: o acesso geralmente é limitado a algumas pessoas. Você pode usar assinatura atrasada durante o desenvolvimento. Para obter mais informações, consulte [Assinando um assembly com atraso](http://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).  
  
## <a name="see-also"></a>Consulte também  
 [Considerações sobre segurança de assembly](http://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067)   
 [Principais conceitos de segurança](http://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98)   
 [Introdução a aplicativos internacionais com base no .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)   
 [Localizando aplicativos](../ide/localizing-applications.md)   
 [Globalizando e localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
