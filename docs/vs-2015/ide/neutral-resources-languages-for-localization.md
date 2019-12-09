---
title: Idiomas de recursos neutros para localização | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- localization [Visual Studio], resources
- NeutralResourcesLanguageAttribute class
- globalization [Visual Studio], resources
- resources [Visual Studio], fallback system
- culture, locating resources
- neutral resources
ms.assetid: ef064995-3b84-4698-a708-9689b7723533
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85e0be0172f27732f8efeb882cbcde5b9c6aef3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670383"
---
# <a name="neutral-resources-languages-for-localization"></a>Idiomas de recursos naturais para localização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A classe <xref:System.Resources.NeutralResourcesLanguageAttribute> especifica a cultura dos recursos incluídos no assembly principal. Esse atributo é usado como um aperfeiçoamento do desempenho, de modo que o objeto <xref:System.Resources.ResourceManager> não pesquise recursos que estão incluídos no assembly principal.

 O código a seguir mostra como definir o idioma de recursos neutros. O código pode ser colocado em um script de build ou no arquivo AssemblyInfo.vb ou AssemblyInfo.cs.

```vb
' Set neutral resources language for assembly.
<Assembly: NeutralResourcesLanguageAttribute("en")>

```

```csharp
// Set neutral resources language for assembly.
[assembly: NeutralResourcesLanguageAttribute("en")]
```

## <a name="see-also"></a>Veja também
 <xref:System.Resources.ResourceManager> [introdução aos aplicativos internacionais com base na](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [organização .NET Framework hierárquica de recursos para localização](../ide/hierarchical-organization-of-resources-for-localization.md) de [aplicativos que localizam](../ide/localizing-applications.md) [globalização e localização de aplicativos](../ide/globalizing-and-localizing-applications.md)
