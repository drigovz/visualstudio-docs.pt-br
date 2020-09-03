---
title: Estrutura VSPackage (controle do código-fonte VSPackage) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, structure
- source control packages, VSPackage overview
ms.assetid: 92722be7-b397-48c3-a7a7-0b931a341961
caps.latest.revision: 27
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08bb0a296daca0de1c02b905a75fb10ce05f254e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68206002"
---
# <a name="vspackage-structure-source-control-vspackage"></a>Estrutura do VSPackage (VSPackage de controle do código-fonte)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O SDK do pacote de controle do código-fonte fornece diretrizes para criar um VSPackage que permite que um implementador de controle do código-fonte integre sua funcionalidade de controle do código-fonte ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente. Um VSPackage é um componente COM que normalmente é carregado sob demanda pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ambiente de desenvolvimento integrado (IDE) com base nos serviços anunciados pelo pacote em suas entradas de registro. Cada VSPackage deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> . Um VSPackage normalmente consome os serviços oferecidos pelo [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE e proffers alguns serviços próprios.  
  
 Um VSPackage declara seus itens de menu e estabelece um estado de item padrão por meio do arquivo. vsct. O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE exibe os itens de menu nesse estado até que o VSPackage seja carregado. Subsequentemente, a implementação do VSPackage do <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> método é chamada para habilitar ou Desabilitar itens de menu.  
  
## <a name="source-control-package-characteristics"></a>Características do pacote de controle do código-fonte  
 Um VSPackage de controle do código-fonte está profundamente integrado ao [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 A semântica VSPackage inclui:  
  
- Interface a ser implementada em virtude de ser um VSPackage (a `IVsPackage` interface)  
  
- Implementação do comando de interface do usuário (arquivo. vsct e implementação da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface)  
  
- Registro do VSPackage com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
  O VSPackage de controle do código-fonte deve se comunicar com essas outras [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entidades:  
  
- Projetos  
  
- Editores  
  
- Soluções  
  
- Windows  
  
- A tabela de documentos em execução  
  
### <a name="visual-studio-environment-services-that-may-be-consumed"></a>Serviços de ambiente do Visual Studio que podem ser consumidos  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>  
  
 Serviço SVsRegisterScciProvider  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsQueryEditQuerySave>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackProjectDocuments>  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsSccManager>  
  
### <a name="vsip-interfaces-implemented-and-called"></a>Interfaces VSIP implementadas e chamadas  
 Um pacote de controle do código-fonte é um VSPackage e, portanto, pode interagir diretamente com outros VSPackages registrados com o [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Para fornecer a amplitude completa da funcionalidade de controle do código-fonte, um VSPackage de controle do código-fonte pode lidar com interfaces fornecidas por projetos ou pelo shell.  
  
 Cada projeto no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] deve implementar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3> para ser reconhecido como um projeto dentro do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. No entanto, essa interface não é especializada o suficiente para controle do código-fonte. Os projetos que devem estar no controle do código-fonte implementam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> . Essa interface é usada pelo VSPackage de controle do código-fonte para consultar um projeto quanto ao seu conteúdo e fornecer glifos e informações de associação (as informações necessárias para estabelecer uma conexão entre o local do servidor e o local do disco de um projeto que está sob controle do código-fonte).  
  
 O VSPackage de controle do código-fonte implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2> , que por sua vez permite que os projetos se registrem para controle do código-fonte e recuperem seus glifos de status.  
  
 Para obter uma lista completa das interfaces que um VSPackage de controle do código-fonte deve considerar, consulte [serviços e interfaces relacionadas](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Elementos de design](../../extensibility/internals/source-control-vspackage-design-elements.md)   
 [Interfaces e serviços relacionados](../../extensibility/internals/related-services-and-interfaces-source-control-vspackage.md)
