---
title: '&lt;elemento FriendlyName &gt; (desenvolvimento do Office no Visual Studio)'
titleSuffix: ''
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <friendlyName> element
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c04a7a90f32051cc211fece4f27f1f46f8fb92f4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939260"
---
# <a name="ltfriendlynamegt-element-office-development-in-visual-studio"></a>&lt;elemento FriendlyName &gt; (desenvolvimento do Office no Visual Studio)
  O `friendlyName` elemento do `vstov4` namespace armazena o nome que aparece na lista de programas instalados.

## <a name="syntax"></a>Sintaxe

```xml
<friendlyName>
</friendlyName>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `friendlyName` elemento está no `vstov4` namespace. O valor aparece na lista de programas instalados no computador e na caixa de diálogo suplementos do VSTO do COM do Microsoft Office aplicativos.

 O `friendlyName` elemento não tem atributos ou elementos filho.

## <a name="vsto-add-in-example"></a>Exemplo de suplemento do VSTO

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra o `friendlyName` elemento em uma solução de nível de aplicativo implantada usando o [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . Este exemplo de código faz parte de um exemplo maior fornecido em [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstov4:friendlyName>
  ContosoOutlookAddIn
</vstov4:friendlyName>
```

## <a name="see-also"></a>Confira também

- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)