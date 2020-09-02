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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
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

## <a name="see-also"></a>Consulte Também
 <xref:System.Resources.ResourceManager>[Introdução aos aplicativos internacionais com base no .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [organização hierárquica de recursos para localização](../ide/hierarchical-organization-of-resources-for-localization.md) de [localizações de aplicativos](../ide/localizing-applications.md) [Globalizando e Localizando aplicativos](../ide/globalizing-and-localizing-applications.md)
