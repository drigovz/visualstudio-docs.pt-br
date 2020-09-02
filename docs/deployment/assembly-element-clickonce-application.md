---
title: '&lt;&gt;elemento assembly (aplicativo ClickOnce) | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assembly> element [ClickOnce application manifest]
ms.assetid: 51410569-10f9-4c0a-96b5-d39185edbefc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b629243920021adc3833f43f268f05638029dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62900754"
---
# <a name="ltassemblygt-element-clickonce-application"></a>&lt;&gt;elemento assembly (aplicativo ClickOnce)
O elemento de nível superior para o manifesto do aplicativo.

## <a name="syntax"></a>Syntax

```xml

      <assembly
   manifestVersion
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `assembly` elemento é o elemento raiz e é necessário. Seu primeiro elemento contido deve ser um `assemblyIdentity` elemento. Os elementos do manifesto devem estar em um dos seguintes namespaces:

 `urn:schemas-microsoft-com:asm.v1`

 `urn:schemas-microsoft-com:asm.v2`

 `http://www.w3.org/2000/09/xmldsig#`

 Os elementos filho do assembly também devem estar nesses namespaces, por herança ou por marcação.

 O `assembly` elemento tem o atributo a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`manifestVersion`|Obrigatórios. O `manifestVersion` atributo deve ser definido como `1.0` .|

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `assembly` elemento em um manifesto de aplicativo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Este exemplo de código é parte de um exemplo maior fornecido no [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).

```xml
<asmv1:assembly
  xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"
  manifestVersion="1.0"
  xmlns:asmv3="urn:schemas-microsoft-com:asm.v3"
  xmlns:dsig=http://www.w3.org/2000/09/xmldsig#
  xmlns:co.v2="urn:schemas-microsoft-com:clickonce.v2"
  xmlns="urn:schemas-microsoft-com:asm.v2"
  xmlns:asmv1="urn:schemas-microsoft-com:asm.v1"
  xmlns:asmv2="urn:schemas-microsoft-com:asm.v2"
  xmlns:xsi=http://www.w3.org/2001/XMLSchema-instance
  xmlns:co.v1="urn:schemas-microsoft-com:clickonce.v1">
```

## <a name="see-also"></a>Confira também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assembly> elementos](../deployment/assembly-element-clickonce-deployment.md)
