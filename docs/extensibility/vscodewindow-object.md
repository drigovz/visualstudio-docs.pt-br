---
title: VsCodeWindow Object | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSCodeWindow
helpviewer_keywords:
- views [Visual Studio SDK], VSCodeWindow object
- VsCodeWindow object
ms.assetid: cf5fe926-e784-4098-bc01-cac49c7c55c6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55739b1ef577123ac0395b4c5cfb1e3c5dbc779f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697952"
---
# <a name="vscodewindow-object"></a>Objeto VSCodeWindow
Uma janela de código é uma janela de documento especializada <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> que pode incluir uma ou mais visualizações de texto, geralmente o objeto.

 Arquiteturalmente, a janela de código é uma janela de documento que está dentro de uma moldura de janela. Funcionalmente, a janela de código é simplesmente uma janela de documento com recursos adicionais. No modo De interface de vários documentos (MDI), a janela de código é o quadro filho MDI. Para obter mais informações, consulte [Personalizar janelas de código usando a API legado](/visualstudio/extensibility/customizing-code-windows-by-using-the-legacy-api?view=vs-2015).

 A tabela a seguir inclui <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow> as interfaces no objeto.

|Método|Descrição|
|------------|-----------------|
|<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>|Fornece um mecanismo de acesso genérico para localizar um serviço que um identificador globalmente único (GUID) identifica.|
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>|Representa uma criança de interface de documento múltiplo (MDI) contendo uma ou mais visualizações de código.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Preenche uma moldura da janela.|

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>
- [Edição de figuras](https://www.microsoft.com/download/details.aspx?id=55984)
