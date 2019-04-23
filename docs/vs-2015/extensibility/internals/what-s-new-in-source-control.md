---
title: Novidades no controle do código-fonte
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio SDK], source control
- source control [Visual Studio SDK], what's new
ms.assetid: bcf85418-18fb-4824-9dae-d14bf3d56a77
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 31b55c57f47f25814eff24f13bcf91408468d0f4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087296"
---
# <a name="what39s-new-in-source-control-in-visual-studio-2015"></a>O que&#39;novo no controle do código-fonte no Visual Studio 2015

[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

No [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] você pode fornecer uma solução de controle do código-fonte profundamente integrado com a implementação de um VSPackage de controle do código-fonte. Esta seção descreve os recursos de controle do código-fonte VSPackages e fornece uma visão geral das etapas de implementação.  
  
## <a name="the-source-control-vspackage"></a>O VSPackage de controle do código-fonte  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] dá suporte a dois tipos de soluções de controle do código-fonte. Todas as versões do [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], você ainda pode integrar uma API de plug-in de controle de origem com base no plug-in. Você também pode criar um VSPackage de controle de origem que fornece uma integração profunda, [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] caminho adequado para soluções de controle do código-fonte que exigem um alto nível de sofisticação e autonomia.  
  
 Um VSPackage pode adicionar praticamente qualquer tipo de funcionalidade para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Um VSPackage de controle do código-fonte fornece um recurso de controle do código-fonte completo para [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], da interface do usuário apresentada ao usuário para a comunicação de back-end com o sistema de controle do código-fonte.  
  
 Implementar um VSPackage de controle do código-fonte exige uma estratégia "tudo ou nada". O criador de um VSPackage de controle do código-fonte deve investir uma quantidade significativa de esforço na implementação de um número de interfaces de controle do código-fonte e os novos elementos de interface do usuário (caixas de diálogo, menus e barras de ferramentas) para cobrir a funcionalidade de controle de origem inteiro, bem como interfaces necessário de qualquer pacote para integrar com êxito com [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 As etapas a seguir dão uma visão geral do que é necessário para implementar um pacote de controle do código-fonte. Para obter detalhes, consulte [criando um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
1. Crie um VSPackage que oferece um serviço de controle de origem particular.  
  
2. Implementar as interfaces nos serviços relacionados ao controle de origem que são dedicaram por [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (por exemplo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider> interface).  
  
3. Registre o VSPackage de controle de origem.  
  
4. Implemente o controle de fonte de todos os da interface do usuário, incluindo itens de menu, caixas de diálogo, barras de ferramentas e menus de contexto.  
  
5. Todos os eventos relacionados ao controle do código-fonte são passados para o controle de origem VSackage quando ele estiver ativo e deve ser tratado pelo VSPackage.  
  
6. O VSPackage de controle de origem deve escutar eventos, como aqueles Implementando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3> interface, bem como eventos de documento de projeto da faixa (TPD) (conforme implementado pelo <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2> interface) e tomar as medidas necessárias.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProvider>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>   
 [Visão geral](../../extensibility/internals/source-control-integration-overview.md)   
 [Criar um VSPackage de controle do código-fonte](../../extensibility/internals/creating-a-source-control-vspackage.md)
