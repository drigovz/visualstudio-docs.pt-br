---
title: Ampliando o Modelo de Objeto do Projeto Base | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708391"
---
# <a name="extend-the-object-model-of-the-base-project"></a>Estender o modelo do projeto base

Um subtipo de projeto pode estender o modelo de objeto de automação do projeto base nos seguintes lugares:

- Project.Extender ("\<ProjectSubtypeName>"): Isso permite que um subtipo de <xref:EnvDTE.Project> projeto ofereça um objeto com métodos personalizados do objeto. Um subtipo de projeto pode usar `Project` extensores de automação para expor o objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo de projeto `VSHPROPID_ExtObjectCATID` <xref:Microsoft.VisualStudio.Shell.Interop.__VSSPROPID2> principal deve `itemid` oferecer seu objeto para o from (correspondente a um valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- ProjectItem.Extender ("\<ProjectSubtypeName>"): Isso permite que um subtipo de <xref:EnvDTE.ProjectItem> projeto ofereça um objeto com métodos personalizados de um determinado objeto dentro do projeto. Um subtipo de projeto pode usar extensores de automação para expor este objeto. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador do subtipo principal do `VSHPROPID_ExtObjectCATID` projeto <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> precisa oferecer seu <xref:Microsoft.VisualStudio.VSConstants.VSITEMID>objeto para o CATID (correspondente a um desejado) .

- Project.Properties: Esta coleção expõe as propriedades `Project` independentes de configuração do objeto. Para obter `Project` mais informações <xref:EnvDTE.Project.Properties%2A>sobre propriedades, consulte . Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a esta coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador de subtipo de projeto `VSHPROPID_BrowseObjectCATID` principal <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> precisa oferecer `itemid` seu objeto para o from (correspondente a um valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)) CATID.

- Configuração.Propriedades: Esta coleção expõe as propriedades dependentes da configuração do projeto para uma configuração específica (por exemplo, Debug). Para obter mais informações, consulte <xref:EnvDTE.Configuration>. Um subtipo de projeto pode usar extensores de automação para adicionar suas propriedades a esta coleção. A <xref:EnvDTE80.IInternalExtenderProvider> interface implementada no agregador do subtipo principal do projeto `VSHPROPID_CfgBrowseObjectCATID` oferece seu `itemid` objeto para o CATID (correspondente a um valor de [VSITEMID. Raiz](<xref:Microsoft.VisualStudio.VSConstants.VSITEMID.Root>)). A <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgBrowseObject> interface é usada para distinguir um objeto de navegação de configuração de outro.

## <a name="see-also"></a>Confira também

- <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID>
