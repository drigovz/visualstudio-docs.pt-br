---
title: '&lt;Cadeias de caracteres&gt; elemento (Bootstrapper) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- MSBuild.GenerateBootstrapper.NoStringsForCulture
- MSBuild.GenerateBootstrapper.ProductCultureNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Strings> element [bootstrapper]
ms.assetid: d5ea3613-5fc9-4a11-bef3-46a01178bf60
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd799020e50121e2f3e9a6ba7ad90fd79a1241cb
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58928408"
---
# <a name="ltstringsgt-element-bootstrapper"></a>&lt;Cadeias de caracteres&gt; elemento (Bootstrapper)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Define as cadeias de caracteres localizadas para nomes de produtos, nomes de pacote e mensagens de erro de instalação.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
<Strings>  
    <String  
        Name  
    >  
    </String>  
</Strings>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O `Strings` um filho do elemento é o `Package` elemento. Ele não tem atributos.  
  
## <a name="string"></a>Cadeia de Caracteres  
 O `String` um filho do elemento é o `Strings` elemento. Um `Strings` elemento pode ter um ou mais `String` elementos.  
  
 `String` tem o seguinte atributo.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Name`|Necessário. O nome da cadeia de caracteres.|  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir especifica que todas as cadeias de caracteres em inglês para o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installer.  
  
```  
<Strings>  
    <String Name="DisplayName">.NET Framework 2.0</String>  
    <String Name="Culture">en</String>  
    <String Name="AdminRequired">Administrator permissions are required to install the .NET Framework 2.0. Contact your administrator.</String>  
    <String Name="InvalidPlatformWin9x">Installation of the .NET Framework 2.0 is not supported on Windows 95. Contact your application vendor.</String>  
    <String Name="InvalidPlatformWinNT">Installation of the .NET Framework 2.0 is not supported on Windows NT 4.0. Contact your application vendor.</String>  
    <String Name="InvalidPlatformIE">Installation of the .NET Framework 2.0 requires Internet Explorer 5.01 or greater. Contact your application vendor.</String>  
    <String Name="InvalidPlatformArchitecture">This version of the .NET Framework 2.0 is not supported on a 64-bit operating system. Contact your application vendor.</String>  
    <String Name="WindowsInstallerImproperInstall">Due to an error with Windows Installer, the installation of the .NET Framework 2.0 cannot proceed.</String>  
    <String Name="AnotherInstanceRunning">Another instance of setup is already running. The running instance must complete before this setup can proceed.</String>  
    <String Name="BetaNDPFailure">A beta version of the .NET Framework was detected on the computer. Uninstall any previous beta versions of .NET Framework before continuing.</String>  
    <String Name="GeneralFailure">A failure occurred attempting to install the .NET Framework 2.0.</String>  
    <String Name="DotNetFXExe">http://go.microsoft.com/fwlink/?LinkId=37283</String>  
    <String Name="InstMsiAExe">http://go.microsoft.com/fwlink/?LinkId=37285</String>  
    <String Name="Msi30Exe">http://go.microsoft.com/fwlink/?LinkId=37287</String>  
</Strings>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Elemento \<Package>](../deployment/package-element-bootstrapper.md)
