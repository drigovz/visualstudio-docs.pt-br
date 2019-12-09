---
title: Classes de estrutura de pacote gerenciado | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297695"
---
# <a name="managed-package-framework-classes"></a>Classes de estrutura de pacote gerenciado
As classes do MPF (estrutura de pacote gerenciada) podem ser usadas para criar VSPackages usando código gerenciado. Eles fornecem implementações padrão para muitas interfaces VSPackage. Ao ocultar os detalhes da implementação e as complexidades, o MPF permite que você crie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] produtos de integração com uma quantidade mínima de código.  
  
> [!WARNING]
> A maioria dos assemblies que contêm classes de estrutura de pacote gerenciada é fornecida com o SDK do Visual Studio. Você pode baixar o código-fonte da estrutura empacotada gerenciada para projetos em [estrutura de pacote gerenciado para projetos](https://archive.codeplex.com/?p=mpfproj11).  
  
## <a name="mpf-namespaces"></a>Namespaces do MPF  
 A tabela a seguir lista os namespaces do MPF fornecidos pelo [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Espaço de nome|{1&gt;Conteúdo&lt;1}|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contém classes úteis para manipular erros COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] constantes e janelas Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Inclui wrappers de código gerenciado para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projetos, editores e MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Inclui classes base do MPF da qual você pode derivar uma implementação de muitos objetos comuns do Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contém extensões do designer de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensões do designer de serialização.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contém [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] as extensões do designer de CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Dá suporte a subtipos de projeto (também conhecidos como "tipos").|  
  
## <a name="see-also"></a>Consulte também  
 [VSPackages e a estrutura de pacote gerenciada](../misc/vspackages-and-the-managed-package-framework.md)   
 [Usando assemblies de interoperabilidade do Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Os VSPackages e a estrutura de pacote gerenciado](../misc/vspackages-and-the-managed-package-framework.md)