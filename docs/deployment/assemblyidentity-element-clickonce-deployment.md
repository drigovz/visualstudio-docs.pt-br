---
title: '&lt;&gt;elemento AssemblyIdentity (implantação do ClickOnce) | Microsoft Docs'
description: O elemento assemblyIdentity é necessário na implantação do ClickOnce. Ele não contém nenhum elemento filho e tem atributos descritos neste artigo.
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
- <assemblyIdentity> element [ClickOnce deployment manifest]
ms.assetid: f4a3bb83-c800-47d0-9905-9a5ae2486838
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5a692d37771070f1835fc791515d5dbc24ce6b1b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383177"
---
# <a name="ltassemblyidentitygt-element-clickonce-deployment"></a>&lt;&gt;elemento AssemblyIdentity (implantação do ClickOnce)
Identifica o assembly primário do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.

## <a name="syntax"></a>Sintaxe

```xml

      <assemblyIdentity  
   name 
   version
   publicKeyToken
   processorArchitecture
    type
/>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `assemblyIdentity` elemento é obrigatório. Ele não contém nenhum elemento filho e tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Obrigatórios. Identifica o nome legível da implantação para fins informativos.<br /><br /> Se `name` o contiver caracteres especiais, como aspas simples ou duplas, o aplicativo poderá falhar ao ser ativado.|
|`version`|Obrigatórios. Especifica o número de versão do assembly, no seguinte formato: `major.minor.build.revision` .<br /><br /> Esse valor deve ser incrementado em um manifesto atualizado para disparar uma atualização de aplicativo.|
|`publicKeyToken`|Obrigatórios. Especifica uma cadeia de caracteres hexadecimal de 16 caracteres que representa os últimos 8 bytes do valor de hash SHA-1 da chave pública sob a qual o manifesto de implantação é assinado. A chave pública usada para assinar deve ter 2048 bits ou mais.<br /><br /> Embora a assinatura de um assembly seja recomendada, mas opcional, esse atributo é necessário. Se um assembly não estiver assinado, você deverá copiar um valor de um assembly autoassinado ou usar um valor "fictício" de todos os zeros.|
|`processorArchitecture`|Obrigatórios. Especifica o processador. Os valores válidos são `msil` para todos os processadores, `x86` para o windows de 32 bits, `IA64` para o Windows de 64 bits e `Itanium` para processadores Intel de 64 bits Itanium.|
|`type`|Obrigatórios. Para compatibilidade com a tecnologia de instalação lado a lado do Windows. O único valor permitido é `win32` .|

## <a name="remarks"></a>Comentários

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `assemblyIdentity` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação. Este exemplo de código faz parte de um exemplo maior fornecido para o tópico [manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md) .

```xml
<!-- Identify the deployment. -->
<assemblyIdentity
  name="My Application Deployment.app"
  version="1.0.0.0"
  publicKeyToken="43cb1e8e7a352766"
  language="neutral"
  processorArchitecture="x86"
  xmlns="urn:schemas-microsoft-com:asm.v1" />
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<assemblyIdentity> elementos](../deployment/assemblyidentity-element-clickonce-application.md)