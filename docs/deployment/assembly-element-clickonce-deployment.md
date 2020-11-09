---
title: '&lt;&gt;elemento assembly (implantação do ClickOnce) | Microsoft Docs'
description: O elemento assembly é o elemento raiz e é necessário na implantação do ClickOnce. Seu primeiro elemento contido deve ser um elemento assemblyIdentity.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce deployment manifest]
ms.assetid: b8e3362a-f821-4696-b98d-571d4bbfe431
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dde3bdb5fc0e9c6ea256aaa4368623a8e8af18d6
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383229"
---
# <a name="ltassemblygt-element-clickonce-deployment"></a>&lt;&gt;elemento assembly (implantação do ClickOnce)
O elemento de nível superior para o manifesto de implantação.

## <a name="syntax"></a>Sintaxe

```xml

      <assembly  
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `assembly` elemento é o elemento raiz e é necessário. Seu primeiro elemento contido deve ser um `assemblyIdentity` elemento. Os elementos do manifesto devem estar nos seguintes namespaces: `urn:schemas-microsoft-com:asm.v1` , `urn:schemas-microsoft-com:asm.v2` e `http://www.w3.org/2000/09/xmldsig#` . Os elementos filho do assembly também devem estar nesses namespaces, por herança ou por marcação.

 O `assembly` elemento tem o atributo a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`manifestVersion`|Obrigatórios. Esse atributo deve ser definido como `1.0` .|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `assembly` elemento em um manifesto de implantação para um aplicativo implantado usando o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Este exemplo de código faz parte de um exemplo maior fornecido para o tópico [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1"
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xrml="urn:mpeg:mpeg21:2003:01-REL-R-NS"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assembly> elementos](../deployment/assembly-element-clickonce-application.md)