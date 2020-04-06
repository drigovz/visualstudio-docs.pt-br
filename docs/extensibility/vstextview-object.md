---
title: VsTextView Object | Microsoft Docs
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
ms.openlocfilehash: 81d5e02d6ec18f8561a83b414532a4b78def5c09
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697708"
---
# <a name="vstextview-object"></a>Objeto VSTextView

A exibição de texto é uma janela que permite aos usuários visualizar e editar o texto Unicode do buffer de texto. Essencialmente, a visão é o que a maioria dos usuários se refere como o editor. Como a exibição é separada do buffer por várias camadas de texto (envoltório de palavras, delineamento de texto e assim por diante), a exibição não é garantida como uma representação exata do texto no buffer. Para obter mais informações sobre a exibição de texto, consulte [Acessando a exibiçãoText usando a API legado](/visualstudio/extensibility/accessing-thetext-view-by-using-the-legacy-api?view=vs-2015).

A tabela a seguir mostra <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> as interfaces no objeto.

|Interface|Descrição|
|---------------|-----------------|
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Interface OLE padrão.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Permite a criação de ações compostas (ou seja, ações agrupadas em uma única unidade de desfazer/refazer).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Fornece os métodos básicos para gerenciar e acessar a visualização. `IVsTextView`não é seguro roscado.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Cria e gerencia um painel de janelas.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interage com camadas de texto.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Executa operações na vista a partir de um segmento diferente.|

## <a name="see-also"></a>Confira também

- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
- [Objeto VSTextBuffer](../extensibility/vstextbuffer-object.md)
