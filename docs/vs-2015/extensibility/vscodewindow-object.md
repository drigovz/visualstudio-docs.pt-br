---
title: Objeto VSCodeWindow | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1711b1409e42d431ad34badf82cff68e5a9bad75
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926377"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma janela de código é uma janela de documento especializado que pode incluir uma ou mais exibições de texto, geralmente o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro filho MDI. Para obter mais informações, consulte [Personalizando o Windows de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 A tabela a seguir inclui as interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que identifica um identificador global exclusivo (GUID).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa um filho de MDI (interface MDI) vários documentos que contém um ou mais modos de exibição de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edição de figuras](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
