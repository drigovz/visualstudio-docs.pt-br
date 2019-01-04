---
title: '&lt;ponto de entrada&gt; elemento (desenvolvimento do Office no Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <entryPoint> element
- <entryPoint> element
- entryPoint element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: c99b6b052fcb411d3f5972d174f804f3000faabe
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53902052"
---
# <a name="ltentrypointgt-element-office-development-in-visual-studio"></a>&lt;ponto de entrada&gt; elemento (desenvolvimento do Office no Visual Studio)
  Cada `entryPoint` elemento do `vstav3` namespace identifica um assembly de personalização que deve ser executado quando isso [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] aplicativo está instalado.

## <a name="syntax"></a>Sintaxe

```xml
<entryPoint class>
    <assemblyIdentity />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `entryPoint` elemento é necessário e está no `vstav3` namespace.

 Cada `entryPoint` elemento pode conter apenas um assembly de personalização. Pode haver vários `entryPoint` elementos definidos em um manifesto de aplicativo.

 O `entryPoint` elemento tem os seguintes atributos.

|Atributo|Descrição|
|---------------|-----------------|
|`class`|Necessário. Identifica um assembly de personalização a ser executado. A sintaxe para esse atributo é *NamespaceName.ClassName*.|

 `entryPoint` tem o seguinte elemento.

### <a name="assemblyidentity"></a>assemblyIdentity
 Necessário. O `assemblyIdentity` elemento na `vstav3` namespace refere-se a um existente `assemblyIdentity` elemento no [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] manifesto do aplicativo.

 A função de `assemblyIdentity` e seus atributos é definida no [ &#60;assemblyIdentity&#62; elemento &#40;aplicativo ClickOnce&#41;](../deployment/assemblyidentity-element-clickonce-application.md).

## <a name="document-level-customization-example"></a>Exemplo de personalização no nível de documento

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra `entryPoint` elementos em um aplicativo de manifesto para uma solução do Office em nível de documento implantada usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:entryPoint
  class="ContosoExcelWorkbook.ThisWorkbook">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet1">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet2">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
<vstav3:entryPoint
  class="ContosoExcelWorkbook.Sheet3">
  <assemblyIdentity
    name="ContosoExcelWorkbook"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra uma `entryPoint` elemento em um manifesto de aplicativo para uma solução do Office de nível de aplicativo implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:entryPoint
  class="ContosoOutlookAddIn.ThisAddIn">
  <assemblyIdentity
    name="ContosoOutlookAddIn"
    version="1.0.0.0"
    language="neutral"
    processorArchitecture="msil" />
</vstav3:entryPoint>
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)