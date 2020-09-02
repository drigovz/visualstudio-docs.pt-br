---
title: Estendendo o modelo de objeto do projeto base | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7723881bce81824b66a936793175077a0ec67666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187161"
---
# <a name="extending-the-object-model-of-the-base-project"></a>Estendendo o modelo de objeto do projeto base
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes locais:  
  
- Project. Extender (" \<ProjectSubtypeName> ") – isso permite que um subtipo de projeto ofereça um objeto com métodos personalizados do <xref:EnvDTE.Project> . Um subtipo de projeto pode usar extensores de automação para expor o `Project` objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal deve oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` do <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> CATID (correspondente a um `itemid` valor de VSITEMID_ROOT, from `VSITEMID` ).  
  
- ProjectItem. Extender (" \<ProjectSubtypeName> ") – isso permite que um subtipo de projeto ofereça um objeto com métodos personalizados de um <xref:EnvDTE.ProjectItem> objeto específico dentro do projeto. Um subtipo de projeto pode usar extensores de automação para expor esse objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para `VSHPROPID_ExtObjectCATID` o <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID de (correspondente a um desejado `VSITEMID` ).  
  
- Project. Properties – essa coleção expõe as propriedades independentes de configuração do `Project` objeto. Para obter mais informações sobre as propriedades do projeto, consulte <xref:EnvDTE.Project.Properties%2A> . Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a essa coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para o `VSHPROPID_BrowseObjectCATID` de VSHPROPID2 (correspondente a um `itemid` valor de VSITEMID_ROOT, from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> ) CATID.  
  
- Configuration. Properties – essa coleção expõe as propriedades dependentes de configuração do projeto para uma configuração específica (por exemplo, debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a essa coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal oferece seu objeto para o CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondente a um `itemid` valor de <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ). A <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface é usada para distinguir um objeto de procura de configuração de outro.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
