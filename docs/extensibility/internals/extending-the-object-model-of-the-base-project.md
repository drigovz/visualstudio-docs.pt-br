---
title: Estendendo o modelo de objeto do projeto base | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- automation object model, extending
- project subtypes, extending automation object model
- automation object model
ms.assetid: 2f95cc53-dff6-476c-bacd-500fb0ff7725
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33186cd477ade7f562f6191393dabe8e94f4f194
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708391"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estender o modelo de objeto do projeto base

Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes locais:

- Project. Extender (" \<ProjectSubtypeName> "): isso permite que um subtipo de projeto ofereça um objeto com métodos personalizados do <xref:EnvDTE.Project> objeto. Um subtipo de projeto pode usar extensores de automação para expor o `Project` objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal deve oferecer seu objeto para o `VSHPROPID_ExtObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem. Extender (" \<ProjectSubtypeName> "): isso permite que um subtipo de projeto ofereça um objeto com métodos personalizados de um <xref:EnvDTE.ProjectItem> objeto específico dentro do projeto. Um subtipo de projeto pode usar extensores de automação para expor esse objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para `VSHPROPID_ExtObjectCATID` o <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> CATID de (correspondente a um desejado <xref:Microsoft.VisualStudio.VSConstants.VSITEMID> ).

- Project. Properties: essa coleção expõe as propriedades independentes de configuração do `Project` objeto. Para obter mais informações sobre `Project` Propriedades, consulte <xref:EnvDTE.Project.Properties%2A> . Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a essa coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal precisa oferecer seu objeto para o `VSHPROPID_BrowseObjectCATID` from <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuration. Properties: essa coleção expõe as propriedades dependentes da configuração do projeto para uma configuração específica (por exemplo, debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a essa coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo do projeto principal oferece seu objeto para o CATID `VSHPROPID_CfgBrowseObjectCATID` (correspondente a um `itemid` valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). A <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface é usada para distinguir um objeto de procura de configuração de outro.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
