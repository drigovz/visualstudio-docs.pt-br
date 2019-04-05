---
title: Objeto VSTextView | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e8ed14761b77e3469b2c19d0e9fd2ff3732bb72d
ms.sourcegitcommit: 447f2174bdecdd471d8a8e11c19554977db620a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2019
ms.locfileid: "58999922"
---
# <a name="vstextview-object"></a>Objeto VSTextView
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição de texto é uma janela que permite aos usuários exibir e editar o texto Unicode de buffer de texto. Essencialmente, o modo de exibição é que se refere a maioria dos usuários como o editor. Porque o modo de exibição é separado do buffer por várias camadas de texto (quebra automática de linha, estrutura de tópicos de texto e assim por diante), o modo de exibição não é garantido para ser uma representação exata do texto no buffer. Para obter mais informações sobre a exibição de texto, consulte [acessando theText exibição usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 A tabela a seguir mostra as interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE padrão.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações que são agrupadas em uma unidade de desfazer/refazer único).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornece os métodos básicos para gerenciar e acessar o modo de exibição. `IVsTextView` não é thread-safe.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Cria e gerencia um painel de janela.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interage com as camadas de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Executa operações no modo de exibição de um thread diferente.|  
  
## <a name="see-also"></a>Consulte também  
 [Edição de figuras](http://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)   
 [Acessando a exibição de texto usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
