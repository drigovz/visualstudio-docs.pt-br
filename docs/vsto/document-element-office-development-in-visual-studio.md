---
title: '&lt;documento&gt; elemento (desenvolvimento do Office no Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document element
- application manifests [Office development in Visual Studio], <document> element
- <document> element
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2c1798815ee3216d6f3bb41eae70ae3e2cdc0121
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854744"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;documento&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `document` elemento o `vstov4` namespace armazena informações de personalização específicas para personalizações no nível do documento.

## <a name="syntax"></a>Sintaxe

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 Necessário apenas para personalizações no nível do documento. O `document` elemento está na `vstov4` namespace. O `document` elemento tem os seguintes atributos.

|Atributo|Descrição|
|---------------|-----------------|
|`solutionId`|Necessário. O GUID usado pelo Visual Studio Tools para Office runtime para identificar exclusivamente uma solução de nível de documento. Esse valor é armazenado como propriedade assemblylocation personalizada de documento. Para obter mais informações, consulte [visão geral das propriedades de documento personalizado](../vsto/custom-document-properties-overview.md).|

 `document` não tem elementos filho.

## <a name="document-level-customization-example"></a>Exemplo de personalização no nível de documento

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra a `document` elemento em uma solução do Office em nível de documento implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)