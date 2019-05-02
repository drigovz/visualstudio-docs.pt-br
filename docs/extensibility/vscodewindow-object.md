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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b1a3c19d349b84b10e0f36aca57a24aaac0d521
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953121"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Uma janela de código é uma janela de documento especializado que pode incluir uma ou mais exibições de texto, geralmente o <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> objeto.

 Em termos de arquitetura, a janela de código é uma janela de documento que está dentro de um quadro de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo de interface de documentos múltiplos (MDI), a janela de código é o quadro filho MDI. Para obter mais informações, consulte [personalização do windows de código usando a API herdada](../extensibility/customizing-code-windows-by-using-the-legacy-api.md).

 A tabela a seguir inclui as interfaces no <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> objeto.

|Método|Descrição|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que identifica um identificador global exclusivo (GUID).|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa um filho de MDI (interface MDI) vários documentos que contém um ou mais modos de exibição de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche um quadro de janela.|

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)