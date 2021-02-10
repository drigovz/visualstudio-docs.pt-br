---
title: '&lt;&gt;elemento Document (desenvolvimento do Office no Visual Studio)'
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e92c17d71b1c0959cb1918ce6fbad0e2cd44d5ec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949825"
---
# <a name="ltdocumentgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento Document (desenvolvimento do Office no Visual Studio)
  O `document` elemento do `vstov4` namespace armazena informações específicas de personalização para personalizações em nível de documento.

## <a name="syntax"></a>Sintaxe

```xml
<document solutionId />
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 Necessário apenas para personalizações em nível de documento. O `document` elemento está no `vstov4` namespace. O `document` elemento tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`solutionId`|Obrigatórios. O GUID usado pelo Ferramentas do Visual Studio para o tempo de execução do Office identificar exclusivamente uma solução em nível de documento. Esse valor é armazenado como a propriedade de documento personalizada _AssemblyLocation. Para obter mais informações, consulte [visão geral de propriedades de documento personalizadas](../vsto/custom-document-properties-overview.md).|

 `document` Não tem nenhum elemento filho.

## <a name="document-level-customization-example"></a>Exemplo de personalização no nível do documento

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra o `document` elemento em uma solução do Office de nível de documento implantada usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Este exemplo de código faz parte de um exemplo maior fornecido em [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:document
  solutionId="73e" />
```

## <a name="see-also"></a>Confira também

- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)