---
title: Manifesto de implantação do ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce, deployment manifests
- deployment manifests [ClickOnce]
ms.assetid: 8457e615-e3b6-4990-8dcf-11bc590e4e9b
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5d1fe2191dadd0972dcde6f38b9697e29f05ab8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68190471"
---
# <a name="clickonce-deployment-manifest"></a>Manifesto de implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um manifesto de implantação é um arquivo XML que descreve uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação, incluindo a identificação da versão atual do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo a ser implantada.  
  
 Os manifestos de implantação têm os seguintes elementos e atributos.  
  
|Elemento|Descrição|Atributos|  
|-------------|-----------------|----------------|  
|[\<assembly> Elementos](../deployment/assembly-element-clickonce-deployment.md)|Obrigatórios. Elemento de nível superior.|`manifestVersion`|  
|[\<assemblyIdentity> Elementos](../deployment/assemblyidentity-element-clickonce-deployment.md)|Obrigatórios. Identifica o manifesto do aplicativo para o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo.|`name`<br /><br /> `version`<br /><br /> `publicKeyToken`<br /><br /> `processorArchitecture`<br /><br /> `culture`|  
|[\<description> Elementos](../deployment/description-element-clickonce-deployment.md)|Obrigatórios. Identifica as informações do aplicativo usadas para criar uma presença de shell e o item **Adicionar ou remover programas** no painel de controle.|`publisher`<br /><br /> `product`<br /><br /> `supportUrl`|  
|[\<deployment> Elementos](../deployment/deployment-element-clickonce-deployment.md)|Opcional. Identifica os atributos usados para a implantação de atualizações e a exposição ao sistema.|`install`<br /><br /> `minimumRequiredVersion`<br /><br /> `mapFileExtensions`<br /><br /> `disallowUrlActivation`<br /><br /> `trustUrlParameters`|  
|[\<compatibleFrameworks> Elementos](../deployment/compatibleframeworks-element-clickonce-deployment.md)|Obrigatórios. Identifica as versões do .NET Framework em que esse aplicativo pode ser instalado e executado.|`SupportUrl`|  
|[\<dependency> Elementos](../deployment/dependency-element-clickonce-deployment.md)|Obrigatórios. Identifica a versão do aplicativo a ser instalada para a implantação e o local do manifesto do aplicativo.|`preRequisite`<br /><br /> `visible`<br /><br /> `dependencyType`<br /><br /> `codebase`<br /><br /> `size`|  
|[\<publisherIdentity> Elementos](../deployment/publisheridentity-element-clickonce-deployment.md)|Necessário para manifestos assinados. Contém informações sobre o Publicador que assinou este manifesto de implantação.|`Name`<br /><br /> `issuerKeyHash`|  
|[\<Signature> Elementos](../deployment/signature-element-clickonce-deployment.md)|Opcional. Contém as informações necessárias para assinar digitalmente este manifesto de implantação.|Nenhum|  
|[\<customErrorReporting> Elementos](../deployment/customerrorreporting-element-clickonce-deployment.md)|Opcional. Especifica um URI para mostrar quando ocorre um erro.|Uri|  
  
## <a name="remarks"></a>Comentários  
 O arquivo de manifesto de implantação identifica uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação de aplicativo, incluindo a versão atual e outras configurações de implantação. Ele faz referência ao manifesto do aplicativo, que descreve a versão atual do aplicativo e todos os arquivos contidos na implantação.  
  
 Para obter mais informações, consulte [Segurança e implantação do ClickOnce](../deployment/clickonce-security-and-deployment.md).  
  
## <a name="file-location"></a>Local do arquivo  
 O arquivo de manifesto de implantação faz referência ao manifesto do aplicativo correto para a versão atual do aplicativo. Ao disponibilizar uma nova versão de uma implantação de aplicativo, você deve atualizar o manifesto de implantação para fazer referência ao novo manifesto do aplicativo.  
  
 O arquivo de manifesto de implantação deve ter um nome forte e também pode conter certificados para validação do Publicador.  
  
## <a name="file-name-syntax"></a>Sintaxe de nome de arquivo  
 O nome de um arquivo de manifesto de implantação deve terminar com a extensão. Application.  
  
## <a name="examples"></a>Exemplos  
 O exemplo de código a seguir ilustra um manifesto de implantação.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly xsi:schemaLocation="urn:schemas-microsoft-com:asm.v1 assembly.adaptive.xsd"  
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
  <assemblyIdentity   
    name="My Application Deployment.app"  
    version="1.0.0.0"  
    publicKeyToken="43cb1e8e7a352766"  
    language="neutral"  
    processorArchitecture="x86"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <description  
    asmv2:publisher="My Company Name"  
    asmv2:product="My Application"  
    xmlns="urn:schemas-microsoft-com:asm.v1" />  
  <deployment install="true">  
    <subscription>  
      <update>  
        <expiration maximumAge="0" unit="days" />  
      </update>  
    </subscription>  
    <deploymentProvider codebase="\\myServer\sampleDeployment\MyApplicationDeployment.application" />  
  </deployment>  
  <compatibleFrameworks xmlns="urn:schemas-microsoft-com:clickonce.v2">  
    <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.20506" />  
    <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.20506" />  
  </compatibleFrameworks>  
  <dependency>  
    <dependentAssembly  
      dependencyType="install"  
      codebase="1.0.0.0\My Application Deployment.exe.manifest"  
      size="6756">  
      <assemblyIdentity  
        name="My Application Deployment.exe"  
        version="1.0.0.0"  
        publicKeyToken="43cb1e8e7a352766"  
        language="neutral"  
        processorArchitecture="x86"  
        type="win32" />  
      <hash>  
        <dsig:Transforms>  
          <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
        </dsig:Transforms>  
        <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
        <dsig:DigestValue>E506x9FwNauks7UjQywmzgtd3FE=</dsig:DigestValue>  
      </hash>  
    </dependentAssembly>  
  </dependency>  
<publisherIdentity name="CN=DOMAIN\MyUsername" issuerKeyHash="18312a18a21b215ecf4cdb20f5a0e0b0dd263c08" /><Signature Id="StrongNameSignature" xmlns="http://www.w3.org/2000/09/xmldsig#">  
…  
</Signature></asmv1:assembly>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)
