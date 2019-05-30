---
title: Objeto VSTextView | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eddd5640b2f8f073f791f6bdb4dc006f8fab0e36
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322822"
---
# <a name="vstextview-object"></a>Objeto VSTextView
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
- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)
- [Modo de exibição theText acessando usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)