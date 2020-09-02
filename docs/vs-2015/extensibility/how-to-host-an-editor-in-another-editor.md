---
title: Como hospedar um editor em outro editor | Microsoft Docs
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
ms.openlocfilehash: 4d4b4ff425feb22b5057a8d1a76b7f73b8932d9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204176"
---
# <a name="how-to-host-an-editor-in-another-editor"></a>Como hospedar um editor em outro editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode hospedar um editor dentro de outro especificando a janela de hospedagem como uma janela pai. Para fazer isso, defina os parâmetros <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> e <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> no quadro da janela filho.  
  
### <a name="to-set-up-the-window-frame-to-host-an-editor"></a>Para configurar o quadro da janela para hospedar um editor  
  
1. Designe um editor como editor hospedado criando um painel de janela filho.  
  
     Esse é o local onde o texto do editor será usado.  
  
2. Crie o editor de hospedagem usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> método ou.  
  
3. Defina as <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID2> Propriedades e na implementação do quadro da janela do editor hospedado passando essas propriedades como os parâmetros para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.SetProperty%2A> método, respectivamente.  
  
     Se você precisar recuperar esses parâmetros, passe essas propriedades para o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> método.  
  
4. Chame o <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> método para o editor contido.  
  
     O editor aparece no painel hospedado do editor que o contém.  
  
## <a name="robust-programming"></a>Programação robusta  
 O **Designer de aplicativos** no Visual Studio Team Edition for Architects é um exemplo de um quadro de janela do editor que hospeda outro editor. O **Designer de aplicativos** hospeda outros designers no seu painel à direita. Um painel de designer (ou página de **Propriedades** ) para cada um dos designers contidos é adicionado ao quadro de janela que o contém.
