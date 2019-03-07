---
title: Estendendo o modelo de objeto do projeto Base | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba6e9de6681b3156aad62ba7f432bef793e0f772
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335669"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estender o modelo de objeto do projeto base

Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes locais:

-   Project.Extender("\<ProjectSubtypeName>"): Isso permite que um subtipo de projeto oferece um objeto com métodos personalizados do <xref:EnvDTE.Project> objeto. Um subtipo de projeto pode usar extensores de automação para expor o `Project` objeto. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada do agregador de subtipo de projeto principal deve oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

-   ProjectItem.Extender("\<ProjectSubtypeName>"): Isso permite que um subtipo de projeto oferece um objeto com métodos personalizados de um determinado <xref:EnvDTE.ProjectItem> objeto dentro do projeto. Um subtipo de projeto pode usar extensores de automação para expor esse objeto. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada do agregador de subtipo de projeto principal precisa oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondente a um desejado <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>) CATID.

-   Project.Properties: Esta coleção expõe as propriedades de configuração independente do `Project` objeto. Para obter mais informações sobre `Project` propriedades, consulte <xref:EnvDTE.Project.Properties%2A>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada do agregador de subtipo de projeto principal precisa oferecer seu objeto para o `VSHPROPID_BrowseObjectCATID` de <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

-   Configuration.Properties: Esta coleção expõe as propriedades dependentes de configuração do projeto para uma configuração específica (por exemplo, Debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades para esta coleção. O <xref:EnvDTE80.IInternalExtenderProvider> interface implementada do agregador de subtipo de projeto principal oferece seu objeto para o CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). O <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface é usada para diferenciar um objeto de configuração de navegação do outro.

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>