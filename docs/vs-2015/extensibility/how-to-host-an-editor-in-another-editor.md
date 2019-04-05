---
title: 'Como: Hospedar um Editor em outro Editor | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - host a nested editor
ms.assetid: 2b0eb705-fe94-4ca8-93e0-9dbd8ce61a44
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 38e47e918683d375f6a6baded2bf946a60020e64
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58925582"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Como: Hospedar um Editor em outro Editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode hospedar um editor dentro de outro, especificando a janela de hospedagem como uma janela pai. Para fazer isso, defina os parâmetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> no quadro de janela filho.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar o quadro de janela para hospedar um editor  
  
1.  Designe um editor como um editor hospedado, criando um painel de janela filho.  
  
     Esse painel é onde irão texto do editor.  
  
2.  Criar o editor de hospedagem usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> ou <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método.  
  
3.  Defina a <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> propriedades em que a implementação do quadro de janela do editor hospedado, passando a essas propriedades como parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.  
  
     Se você precisar recuperar esses parâmetros, passar essas propriedades para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
4.  Chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para o editor independente.  
  
     O editor aparece no painel hospedado do editor do recipiente.  
  
## <a name="robust-programming"></a>Programação robusta  
 O **Application Designer** no Visual Studio Team Edition for Architects é um exemplo de um quadro de janela do editor outro editor de hospedagem. O **Application Designer** hospeda outros designers em seu painel direito. Um painel do designer (ou **propriedades** página) para cada um dos designers contidos é adicionada ao quadro da janela recipiente.
