---
title: Automação para objetos de configuração e SelectedItem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157253"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação de configuração e objetos SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Você pode automatizar os processos de compilação e item selecionado no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automação para compilações  
 A compilação ou configuração tem um modelo de automação que é fornecido quando você implementa o <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Para obter mais informações, consulte [Understanding Build Configurations (Noções básicas sobre configurações de build)](../../ide/understanding-build-configurations.md).  
  
 Se você criar um VSPackage e quiser controlar as opções de configuração, deverá usar o modelo de automação.  
  
## <a name="automation-for-selecteditem"></a>Automação para SelectedItem  
 Você não precisa fornecer uma implementação para o `SelectedItem` objeto porque o Visual Studio contém uma implementação padrão. No entanto, você pode implementar o `SelectedItem` objeto se preferir. Você deve implementar um objeto que contém a `SelectedItem` interface e retornar uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com VSITEMID definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuindo para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Compreendendo as configurações de compilação](../../ide/understanding-build-configurations.md)
