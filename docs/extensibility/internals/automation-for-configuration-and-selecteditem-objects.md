---
title: Automação de configuração e objetos SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60efbb25b0b5b52e1392ce84c16710a78dde7b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919272"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automação para objetos de configuração e SelectedItem
Você pode automatizar a compilação e os processos do item selecionado no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automação de compilações  
 Compilação ou a configuração tem um modelo de automação que é fornecido quando você implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Para obter mais informações, consulte [Compreender configurações de build](../../ide/understanding-build-configurations.md).  
  
 Se você criar um VSPackage e deseja controlar as opções de configuração, você deve usar o modelo de automação.  
  
## <a name="automation-for-selecteditem"></a>Automação para SelectedItem  
 Você não precisa fornecer uma implementação para o `SelectedItem` porque o Visual Studio contém uma implementação padrão do objeto. No entanto, você pode implementar o `SelectedItem` objeto se você preferir. Você deve implementar um objeto que contém o `SelectedItem` da interface e retorna uma resposta a uma chamada para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> método com `VSITEMID` definido como <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuir para o modelo de automação](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Compreender configurações de build](../../ide/understanding-build-configurations.md)