---
title: '&lt;&gt;elemento AssemblyIdentity (aplicativo ClickOnce) | Microsoft Docs'
description: O elemento assemblyIdentity é necessário no aplicativo ClickOnce. Ele não contém nenhum elemento filho e tem atributos descritos neste artigo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <assemblyIdentity> element [ClickOnce application manifest]
ms.assetid: f48e9531-efac-4d11-8166-f63a5ece1ac5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c86d5d1fd1e25b498405197b68efd9553ed64f16
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383203"
---
# <a name="ltassemblyidentitygt-element-clickonce-application"></a>&lt;&gt;elemento AssemblyIdentity (aplicativo ClickOnce)
Identifica o aplicativo implantado em uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação.

## <a name="syntax"></a>Sintaxe

```xml

      <assemblyIdentity
   name
   version
   publicKeyToken
   processorArchitecture
   language
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `assemblyIdentity` elemento é obrigatório. Ele não contém nenhum elemento filho e tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Obrigatórios. Identifica o nome do aplicativo.<br /><br /> Se `Name` o contiver caracteres especiais, como aspas simples ou duplas, o aplicativo poderá falhar ao ser ativado.|
|`Version`|Obrigatórios. Especifica o número de versão do aplicativo no seguinte formato: `major.minor.build.revision`|
|`publicKeyToken`|Opcional. Especifica uma cadeia de caracteres hexadecimal de 16 caracteres que representa os últimos 8 bytes do `SHA-1` valor de hash da chave pública sob a qual o aplicativo ou assembly é assinado. A chave pública usada para assinar o catálogo deve ter 2048 bits ou mais.<br /><br /> Embora a assinatura de um assembly seja recomendada, mas opcional, esse atributo é necessário. Se um assembly não estiver assinado, você deverá copiar um valor de um assembly autoassinado ou usar um valor "fictício" de todos os zeros.|
|`processorArchitecture`|Obrigatórios. Especifica o processador. Os valores válidos são `msil` para todos os processadores, `x86` para o windows de 32 bits, `IA64` para o Windows de 64 bits e `Itanium` para processadores Intel de 64 bits Itanium.|
|`language`|Obrigatórios. Identifica os códigos de linguagem de duas partes (por exemplo, `en-US` ) do assembly. Este elemento está no `asmv2` namespace. Se não for especificado, o padrão será `neutral` .|

## <a name="examples"></a>Exemplos

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra um `assemblyIdentity` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto do aplicativo. Este exemplo de código é parte de um exemplo maior fornecido no [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md).

### <a name="code"></a>Código

```xml
<asmv1:assemblyIdentity
  name="My Application Deployment.exe"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  type="win32" />
```

## <a name="see-also"></a>Confira também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<assemblyIdentity> elementos](../deployment/assemblyidentity-element-clickonce-deployment.md)