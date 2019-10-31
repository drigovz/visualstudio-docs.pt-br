---
title: Objeto VSCodeWindow | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 36b7e0e6806f88efe373dffa3f21ba79baefb281
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189045"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Uma janela de código é uma janela de documento especializada que pode incluir uma ou mais exibições de texto, geralmente o objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>.

 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo MDI (interface de vários documentos), a janela de código é o quadro filho MDI. Para obter mais informações, consulte [Personalizando janelas de código usando a API herdada](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 A tabela a seguir inclui as interfaces no objeto <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>.

|Método|Descrição|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que um GUID (identificador global exclusivo) identifica.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa um filho MDI (interface de vários documentos) que contém uma ou mais exibições de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)