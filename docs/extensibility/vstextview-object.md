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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06e1ba7c10912f23fedc09892e03e2105ff2bab4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583600"
---
# <a name="vstextview-object"></a>Objeto VSTextView

A exibição de texto é uma janela que permite aos usuários exibir e editar o texto Unicode do buffer de texto. Essencialmente, a exibição é o que a maioria dos usuários se refere como o editor. Como a exibição é separada do buffer por várias camadas de texto (quebra automática de palavra, texto de estrutura de tópicos e assim por diante), não há garantia de que a exibição seja uma representação exata do texto no buffer. Para obter mais informações sobre a exibição de texto, consulte [acessando a exibição de texto usando a API herdada](../vs-2015/extensibility/accessing-thetext-view-by-using-the-legacy-api.md?view=vs-2015&preserve-view=true).

A tabela a seguir mostra as interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

|Interface|Descrição|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita a criação de ações compostas (ou seja, ações agrupadas em uma única unidade de desfazer/refazer).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornece os métodos básicos para gerenciar e acessar o modo de exibição. `IVsTextView` Não é thread-safe.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Cria e gerencia um painel de janela.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interage com as camadas de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Executa operações na exibição de um thread diferente.|

## <a name="see-also"></a>Confira também

- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)