---
title: '&lt;&gt;elemento Dependency (implantação do ClickOnce) | Microsoft Docs'
description: O elemento Dependency identifica a versão do aplicativo a ser instalada e o local do manifesto do aplicativo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#osVersionInfo
- urn:schemas-microsoft-com:asm.v2#os
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#dependency
- http://www.w3.org/2000/09/xmldsig#DigestValue
- urn:schemas-microsoft-com:asm.v2#assemblyIdentity
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
- urn:schemas-microsoft-com:asm.v2#dependentAssembly
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <dependency> element [ClickOnce deployment manifest]
ms.assetid: 9b4d2082-0347-4922-ac70-85f11b913039
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 172f3ea546565554c5f0701b81a88b9ca99b4100
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99881094"
---
# <a name="ltdependencygt-element-clickonce-deployment"></a>&lt;&gt;elemento Dependency (implantação do ClickOnce)
Identifica a versão do aplicativo a ser instalada e o local do manifesto do aplicativo.

## <a name="syntax"></a>Sintaxe

```xml

      <dependency>
   <dependentAssembly
      preRequisite
      visible
      dependencyType
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         publicKeyToken
         processorArchitecture
         language
         type
      />
      <hash>
         <dsig:Transforms>
            <dsig:Transform
                Algorithm
            />
         </dsig:Transforms>
         <dsig:DigestMethod />
         <dsig:DigestValue>
         </dsig:DigestValue>
      </hash>

   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `dependency` elemento é obrigatório. Ele não tem atributos. Um manifesto de implantação pode ter vários `dependency` elementos.

 O `dependency` elemento geralmente expressa as dependências para o aplicativo principal em assemblies contidos em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Se seu aplicativo de Main.exe consumir um assembly chamado DotNetAssembly.dll, esse assembly deverá estar listado em uma seção de dependência. No entanto, a dependência também pode expressar outros tipos de dependências, como dependências em uma versão específica do Common Language Runtime, em um assembly no GAC (cache de assembly global) ou em um objeto COM. Como se trata de uma tecnologia de implantação sem intervenção, o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] não pode iniciar o download e a instalação desses tipos de dependências, mas impede que o aplicativo seja executado se uma ou mais das dependências especificadas não existirem.

## <a name="dependentassembly"></a>dependentAssembly
 Obrigatório. Esse elemento contém o `assemblyIdentity` elemento. A tabela a seguir mostra os atributos `dependentAssembly` aos quais o oferece suporte.

| Atributo | Descrição |
|------------------| - |
| `preRequisite` | Opcional. Especifica que esse assembly já deve existir no GAC. Os valores válidos são `true` e `false`. Se `true` e o assembly especificado não existir no GAC, o aplicativo não será executado. |
| `visible` | Opcional. Identifica a identidade de aplicativo de nível superior, incluindo suas dependências. Usado internamente pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] para gerenciar o armazenamento e a ativação do aplicativo. |
| `dependencyType` | Obrigatório. A relação entre essa dependência e o aplicativo. Os valores válidos são:<br /><br /> -   `install`. O componente representa uma instalação separada do aplicativo atual.<br />-   `preRequisite`. O componente é exigido pelo aplicativo atual. |
| `codebase` | Opcional. O caminho completo para o manifesto do aplicativo. |
| `size` | Opcional. O tamanho do manifesto do aplicativo, em bytes. |

## <a name="assemblyidentity"></a>assemblyIdentity
 Obrigatório. Esse elemento é um filho do `dependentAssembly` elemento. O conteúdo de `assemblyIdentity` deve ser o mesmo descrito no manifesto do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. A tabela a seguir mostra os atributos do `assemblyIdentity` elemento.

|Atributo|Descrição|
|---------------|-----------------|
|`Name`|Obrigatórios. Identifica o nome do aplicativo.|
|`Version`|Obrigatório. Especifica o número de versão do aplicativo, no seguinte formato: `major.minor.build.revision`|
|`publicKeyToken`|Obrigatório. Especifica uma cadeia de caracteres hexadecimal de 16 caracteres que representa os últimos 8 bytes do hash SHA-1 da chave pública sob a qual o aplicativo ou assembly é assinado. A chave pública usada para assinar deve ser de 2048 bits ou mais.|
|`processorArchitecture`|Obrigatório. Especifica o microprocessador. Os valores válidos são `x86` para o Windows de 32 bits e `IA64` para o windows de 64 bits.|
|`Language`|Opcional. Identifica os códigos de idioma de duas partes do assembly. Por exemplo, EN-US, que significa inglês (EUA). O padrão é `neutral`. Este elemento está no `asmv2` namespace.|
|`type`|Opcional. Para compatibilidade com versões anteriores do Windows com tecnologia de instalação lado a lado. O único valor permitido é `win32` .|

## <a name="hash"></a>hash
 O `hash` elemento é um filho opcional do `file` elemento. O `hash` elemento não tem atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] usa um hash de algoritmo de todos os arquivos em um aplicativo como uma verificação de segurança para garantir que nenhum dos arquivos seja alterado após a implantação. Se o `hash` elemento não for incluído, essa verificação não será executada. Portanto, omitir o `hash` elemento não é recomendado.

## <a name="dsigtransforms"></a>dsig:Transforms
 O `dsig:Transforms` elemento é um filho obrigatório do `hash` elemento. O `dsig:Transforms` elemento não tem atributos.

## <a name="dsigtransform"></a>dsig:Transform
 O `dsig:Transform` elemento é um filho obrigatório do `dsig:Transforms` elemento. A tabela a seguir mostra os atributos do `dsig:Transform` elemento.

| Atributo | Descrição |
|-------------| - |
| `Algorithm` | O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é `urn:schemas-microsoft-com:HashTransforms.Identity` . |

## <a name="dsigdigestmethod"></a>dsig:DigestMethod
 O `dsig:DigestMethod` elemento é um filho obrigatório do `hash` elemento. A tabela a seguir mostra os atributos do `dsig:DigestMethod` elemento.

| Atributo | Descrição |
|-------------| - |
| `Algorithm` | O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado pelo [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] é `http://www.w3.org/2000/09/xmldsig#sha1` . |

## <a name="dsigdigestvalue"></a>dsig:DigestValue
 O `dsig:DigestValue` elemento é um filho obrigatório do `hash` elemento. O `dsig:DigestValue` elemento não tem atributos. Seu valor de texto é o hash calculado para o arquivo especificado.

## <a name="remarks"></a>Comentários
 Normalmente, os manifestos de implantação têm um único `assemblyIdentity` elemento que identifica o nome e a versão do manifesto do aplicativo.

## <a name="example-1"></a>Exemplo 1
 O exemplo de código a seguir mostra um `dependency` elemento em um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] manifesto de implantação.

```xml
<!-- Identify the assembly dependencies -->
<dependency>
  <dependentAssembly dependencyType="install" allowDelayedBinding="true" codebase="MyApplication.exe" size="16384">
    <assemblyIdentity name="MyApplication" version="0.0.0.0" cultural="neutral" processorArchitecture="msil" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
       <dsig:DigestValue>YzXYZJAvj9pgAG3y8jXUjC7AtHg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="example-2"></a>Exemplo 2
 O exemplo de código a seguir especifica uma dependência em um assembly já instalado no GAC.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="GACAssembly" version="1.0.0.0" language="neutral" processorArchitecture="msil" />
  </dependentAssembly>
</dependency>
```

## <a name="example-3"></a>Exemplo 3
 O exemplo de código a seguir especifica uma dependência em uma versão específica do Common Language Runtime.

```xml
<dependency>
  <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true">
    <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="2.0.50215.0" />
  </dependentAssembly>
</dependency>
```

## <a name="example-4"></a>Exemplo 4
 O exemplo de código a seguir especifica uma dependência do sistema operacional.

```xml
<dependency>
   <dependentOS supportUrl="http://www.microsoft.com" description="Microsoft Windows Operating System">
      <osVersionInfo>
         <os majorVersion="4" minorVersion="10" />
      </osVersionInfo>
   </dependentOS>
</dependency>
```

## <a name="see-also"></a>Confira também
- [Manifesto de implantação do ClickOnce](../deployment/clickonce-deployment-manifest.md)
- [\<dependency> elementos](../deployment/dependency-element-clickonce-application.md)