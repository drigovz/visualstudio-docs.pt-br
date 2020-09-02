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
ms.openlocfilehash: 511c730ec3a11b02d46f5e9c9271c028bb4fa325
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690769"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma janela de código é uma janela de documento especializada que pode incluir uma ou mais exibições de texto, geralmente o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo MDI (interface de vários documentos), a janela de código é o quadro filho MDI. Para obter mais informações, consulte [Personalizando janelas de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).  
  
 A tabela a seguir inclui as interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que um GUID (identificador global exclusivo) identifica.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa um filho MDI (interface de vários documentos) que contém uma ou mais exibições de código.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>   
 [Edição de figuras](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)
