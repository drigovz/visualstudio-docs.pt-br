---
title: Como especificar uma URL de suporte para pré-requisitos individuais em uma implantação do ClickOnce | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, prerequisites
- ClickOnce deployment, URLs
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1907b619bcc616c73d9b9e37af30722c02bf100e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65679965"
---
# <a name="how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment"></a>Como especificar uma URL de suporte para pré-requisitos individuais em uma implantação do ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantação pode testar vários pré-requisitos que devem estar disponíveis no computador cliente para [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] que o aplicativo seja executado. Isso inclui a versão mínima necessária do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , a versão do sistema operacional e todos os assemblies que devem ser pré-instalados no GAC (cache de assembly global). [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]no entanto, o não pode instalar nenhum desses pré-requisitos; se um pré-requisito não for encontrado, ele simplesmente interromperá a instalação e exibirá uma caixa de diálogo explicando por que a instalação falhou.  
  
 Há dois métodos para instalar os pré-requisitos. Você pode instalá-los usando um aplicativo bootstrapper. Como alternativa, você pode especificar uma URL de suporte para pré-requisitos individuais, que será exibida para os usuários na caixa de diálogo se o pré-requisito não for encontrado. A página referenciada por essa URL pode conter links para instruções para instalar o pré-requisito necessário. Se um aplicativo não especificar uma URL de suporte para um pré-requisito individual, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] o exibirá a URL de suporte especificada no manifesto de implantação para o aplicativo como um todo, se ele estiver definido.  
  
 Embora [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , Mage.exe e MageUI.exe possam ser usados para gerar [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] implantações, nenhuma dessas ferramentas dá suporte direto à especificação de uma URL de suporte para pré-requisitos individuais. Este documento descreve como modificar o manifesto do aplicativo de implantação e o manifesto de implantação para incluir essas URLs de suporte.  
  
### <a name="specifying-a-support-url-for-an-individual-prerequisite"></a>Especificando uma URL de suporte para um pré-requisito individual  
  
1. Abra o manifesto do aplicativo (o arquivo. manifest) para seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo em um editor de texto.  
  
2. Para um pré-requisito do sistema operacional, adicione o `supportUrl` atributo ao `dependentOS` elemento:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3. Para obter um pré-requisito para uma determinada versão do Common Language Runtime, adicione o `supportUrl` atributo à `dependentAssembly` entrada que especifica a dependência de Common Language Runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4. Para obter um pré-requisito para um assembly que deve ser pré-instalado no cache de assembly global, defina o `supportUrl` para o `dependentAssembly` elemento que especifica o assembly necessário:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5. Opcional. Para aplicativos direcionados para o .NET Framework 4, abra o manifesto de implantação (o arquivo. Application) para seu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo em um editor de texto.  
  
6. Para um pré-requisito .NET Framework 4, adicione o `supportUrl` atributo ao `compatibleFrameworks` elemento:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7. Depois de alterar manualmente o manifesto do aplicativo, você deve assinar novamente o manifesto do aplicativo usando seu certificado digital, atualizar e assinar novamente o manifesto de implantação. Você deve usar as ferramentas do SDK do Mage.exe ou do MageUI.exe para realizar essa tarefa, pois regenerar esses arquivos usando [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] apaga as alterações manuais. Para obter mais informações sobre como usar Mage.exe para assinar novamente manifestos, consulte [como: assinar novamente manifestos de aplicativo e implantação](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 A URL de suporte não será exibida na caixa de diálogo se o aplicativo estiver marcado para ser executado em confiança parcial.  
  
## <a name="see-also"></a>Consulte Também  
 [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [Walkthrough: Implantando manualmente um aplicativo ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks> Elementos](../deployment/compatibleframeworks-element-clickonce-deployment.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Pré-requisitos de implantação de aplicativo](../deployment/application-deployment-prerequisites.md)
