---
title: Registrando e cancelando o registro de VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1f6bc85fb00c15831dcf1a9f64e4b886272df218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193826"
---
# <a name="registering-and-unregistering-vspackages"></a>Registrando e cancelando o registro de VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você usa atributos para registrar um VSPackage, mas  
  
## <a name="registering-a-vspackage"></a>Registrando um VSPackage  
 Você pode usar atributos para controlar o registro de VSPackages gerenciados. Todas as informações de registro estão contidas em um arquivo. pkgdef. Para obter mais informações sobre o registro baseado em arquivo, consulte [utilitário CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).  
  
 O código a seguir mostra como usar os atributos de registro padrão para registrar seu VSPackage.  
  
```csharp  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]  
public sealed class BasicPackage : Package  
{. . .}  
```  
  
## <a name="unregistering-an-extension"></a>Cancelando o registro de uma extensão  
 Se você estiver experimentando vários VSPackages diferentes e quiser removê-los da instância experimental, bastará executar o comando **Reset** . Procure **redefinir a instância experimental do Visual Studio** na página inicial do computador ou execute este comando na linha de comando:  
  
```vb  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp  
```  
  
 Se você quiser desinstalar uma extensão que você instalou em sua instância de desenvolvimento do Visual Studio, vá para **ferramentas/extensões e atualizações**, localize a extensão e clique em **desinstalar**.  
  
 Se, por algum motivo, nenhum desses métodos obtiver sucesso ao desinstalar a extensão, você poderá cancelar o registro do assembly VSPackage da linha de comando da seguinte maneira:  
  
```  
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg” /unregister <pathToVSPackage assembly>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [VSPackages](../extensibility/internals/vspackages.md)
