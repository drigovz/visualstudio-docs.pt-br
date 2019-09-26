---
title: '&lt;elemento&gt; Dependency (aplicativo ClickOnce) | Microsoft Docs'
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
- manifests [ClickOnce], dependency element
- <dependency> element [ClickOnce application manifest]
ms.assetid: 09d6a1e0-60f8-4fbd-843b-8e49ee3115a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3aa949aa2f8e718ab0209c54a0ea2160c042a4eb
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252488"
---
# <a name="ltdependencygt-element-clickonce-application"></a>&lt;elemento&gt; Dependency (aplicativo ClickOnce)
Identifica uma dependência de plataforma ou assembly que é necessária para o aplicativo.

## <a name="syntax"></a>Sintaxe

```xml

      <dependency>
   <dependentOS
      supportURL
      description
   >
      <osVersionInfo>
         <os
            majorVersion
            minorVersion
            buildNumber
            servicePackMajor
            servicePackMinor
            productType
            suiteType
         />
      </osVersionInfo>
   </dependentOS>
   <dependentAssembly
      dependencyType
      allowDelayedBinding
      group
      codeBase
      size
   >
      <assemblyIdentity
         name
         version
         processorArchitecture
         language
      >
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

      </assemblyIdentity>
   </dependentAssembly>
</dependency>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `dependency` elemento é obrigatório. Pode haver várias instâncias do `dependency` no mesmo manifesto do aplicativo.

 O `dependency` elemento não tem atributos e contém os seguintes elementos filho.

### <a name="dependentos"></a>dependentOS
 Opcional. Contém o `osVersionInfo` elemento. Os `dependentOS` elementos `dependentAssembly` e são mutuamente exclusivos: um ou o outro deve existir para um `dependency` elemento, mas não para ambos.

 `dependentOS`o oferece suporte aos seguintes atributos.

|Atributo|Descrição|
|---------------|-----------------|
|`supportUrl`|Opcional. Especifica uma URL de suporte para a plataforma dependente. Essa URL será mostrada ao usuário se a plataforma necessária for encontrada.|
|`description`|Opcional. Descreve, em forma legível, o sistema operacional descrito pelo `dependentOS` elemento.|

### <a name="osversioninfo"></a>osVersionInfo
 Necessário. Esse elemento é um filho do `dependentOS` elemento e contém o `os` elemento. Este elemento não tem atributos.

### <a name="os"></a>SO
 Necessário. Esse elemento é um filho do `osVersionInfo` elemento. Esse elemento tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`majorVersion`|Necessário. Especifica o número de versão principal do sistema operacional.|
|`minorVersion`|Necessário. Especifica o número de versão secundária do sistema operacional.|
|`buildNumber`|Necessário. Especifica o número de Build do sistema operacional.|
|`servicePackMajor`|Necessário. Especifica o service pack número principal do sistema operacional.|
|`servicePackMinor`|Opcional. Especifica a service pack número secundário do sistema operacional.|
|`productType`|Opcional. Identifica o valor do tipo de produto. Os valores válidos são `server`, `workstation` e `domainController`. Por exemplo, para o Windows 2000 Professional, esse valor de `workstation`atributo é.|
|`suiteType`|Opcional. Identifica um conjunto de produtos disponível no sistema ou o tipo de configuração do sistema. Os valores válidos são `backoffice`, `blade`, `datacenter`, `enterprise`, `home`, `professional`, `smallbusiness`, `smallbusinessRestricted` e `terminal`. Por exemplo, para o Windows 2000 Professional, esse valor de `professional`atributo é.|

### <a name="dependentassembly"></a>dependentAssembly
 Opcional. Contém o `assemblyIdentity` elemento. Os `dependentOS` elementos `dependentAssembly` e são mutuamente exclusivos: um ou o outro deve existir para um `dependency` elemento, mas não para ambos.

 `dependentAssembly`tem os atributos a seguir.

| Atributo | Descrição |
|-----------------------| - |
| `dependencyType` | Necessário. Especifica o tipo de dependência. Os valores válidos são `preprequisite` e `install`. Um `install` assembly é instalado como parte [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do aplicativo. Um `prerequisite` assembly deve estar presente no GAC (cache de assembly global) antes que [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o aplicativo possa ser instalado. |
| `allowDelayedBinding` | Necessário. Especifica se o assembly pode ser carregado programaticamente em tempo de execução. |
| `group` | Opcional. Se o `dependencyType` atributo for definido como `install`, o designará um grupo nomeado de assemblies que serão instalados apenas sob demanda. Para obter mais informações, confira [Passo a passo: Como baixar assemblies sob demanda com a API de implantação do ClickOnce usando o designer](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md).<br /><br /> Se definido como `framework` e o `dependencyType` atributo for definido `prerequisite`como, o designará o assembly como parte do .NET Framework. O cache assemby global (GAC) não é verificado para este assembly durante a instalação no .NET Framework 4 e versões posteriores. |
| `codeBase` | Necessário quando o `dependencyType` atributo é definido como `install`. O caminho para o assembly dependente. Pode ser um caminho absoluto ou um caminho relativo à base de código do manifesto. Esse caminho deve ser um URI válido para que o manifesto do assembly seja válido. |
| `size` | Necessário quando o `dependencyType` atributo é definido como `install`. O tamanho do assembly dependente, em bytes. |

### <a name="assemblyidentity"></a>assemblyIdentity
 Necessário. Esse elemento é um filho do `dependentAssembly` elemento e tem os atributos a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Necessário. Identifica o nome do aplicativo.|
|`version`|Necessário. Especifica o número de versão do aplicativo no seguinte formato:`major.minor.build.revision`|
|`publicKeyToken`|Opcional. Especifica uma cadeia de caracteres hexadecimal de 16 caracteres que representa os últimos 8 bytes `SHA-1` do valor de hash da chave pública sob a qual o aplicativo ou assembly é assinado. A chave pública usada para assinar o catálogo deve ter 2048 bits ou mais.|
|`processorArchitecture`|Opcional. Especifica o processador. Os valores válidos são `x86` para o Windows de 32 bits `I64` e para o Windows de 64 bits.|
|`language`|Opcional. Identifica os códigos de idioma de duas partes, como EN-US, do assembly.|

### <a name="hash"></a>hash
 O `hash` elemento é um filho opcional `assemblyIdentity` do elemento. O `hash` elemento não tem atributos.

 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]usa um hash de algoritmo de todos os arquivos em um aplicativo como uma verificação de segurança, para garantir que nenhum dos arquivos seja alterado após a implantação. Se o `hash` elemento não for incluído, essa verificação não será executada. Portanto, omitir o `hash` elemento não é recomendado.

### <a name="dsigtransforms"></a>dsig:Transforms
 O `dsig:Transforms` elemento é um filho obrigatório `hash` do elemento. O `dsig:Transforms` elemento não tem atributos.

### <a name="dsigtransform"></a>dsig:Transform
 O `dsig:Transform` elemento é um filho obrigatório `dsig:Transforms` do elemento. O `dsig:Transform` elemento tem os atributos a seguir.

| Atributo | Descrição |
|-------------| - |
| `Algorithm` | O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pelo `urn:schemas-microsoft-com:HashTransforms.Identity`é. |

### <a name="dsigdigestmethod"></a>dsig:DigestMethod
 O `dsig:DigestMethod` elemento é um filho obrigatório `hash` do elemento. O `dsig:DigestMethod` elemento tem os atributos a seguir.

| Atributo | Descrição |
|-------------| - |
| `Algorithm` | O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pelo `http://www.w3.org/2000/09/xmldsig#sha1`é. |

### <a name="dsigdigestvalue"></a>dsig:DigestValue
 O `dsig:DigestValue` elemento é um filho obrigatório `hash` do elemento. O `dsig:DigestValue` elemento não tem atributos. Seu valor de texto é o hash calculado para o arquivo especificado.

## <a name="remarks"></a>Comentários
 Todos os assemblies usados pelo seu aplicativo devem ter um `dependency` elemento correspondente. Os assemblies dependentes não incluem assemblies que devem ser pré-instalados no cache de assembly global como assemblies de plataforma.

## <a name="example"></a>Exemplo
 O exemplo de código a `dependency` seguir ilustra os [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] elementos em um manifesto do aplicativo. Este exemplo de código é parte de um exemplo maior fornecido para o tópico [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<dependency>
  <dependentOS>
    <osVersionInfo>
      <os
        majorVersion="4"
        minorVersion="10"
        buildNumber="0"
        servicePackMajor="0" />
    </osVersionInfo>
  </dependentOS>
</dependency>
<dependency>
  <dependentAssembly
    dependencyType="preRequisite"
    allowDelayedBinding="true">
    <assemblyIdentity
      name="Microsoft.Windows.CommonLanguageRuntime"
      version="4.0.20506.0" />
  </dependentAssembly>
</dependency>

<dependency>
  <dependentAssembly
    dependencyType="install"
    allowDelayedBinding="true"
    codebase="MyApplication.exe"
    size="4096">
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <hash>
      <dsig:Transforms>
        <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />
      </dsig:Transforms>
      <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />
      <dsig:DigestValue>DpTW7RzS9IeT/RBSLj54vfTEzNg=</dsig:DigestValue>
    </hash>
  </dependentAssembly>
</dependency>
```

## <a name="see-also"></a>Consulte também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<elemento de > de dependência](../deployment/dependency-element-clickonce-deployment.md)