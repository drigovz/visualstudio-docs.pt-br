---
title: Personalizando janelas de código usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - code windows
ms.assetid: 5328ab2f-55cb-4680-9744-ec79f55acd1b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f15c649b8d857d2e920bb957e5975d296749cb86
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62556108"
---
# <a name="customizing-code-windows-by-using-the-legacy-api"></a>Personalizando o código do Windows usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma janela de código é um objeto de janela de documento que dá suporte a uma ou mais exibições de texto. Os recursos exatos de uma janela de código dependem do serviço de idioma associado. No modo MDI (interface de vários documentos), a janela de código é o quadro filho MDI.  
  
 Janelas de código são controladas por serviços de linguagem, e cada serviço de linguagem pode fornecer seu próprio Gerenciador de janelas de código. Isso permite que o serviço de linguagem adicione seus próprios adornos à janela de código, como rabiscos, colorização e muito mais. Para obter mais informações sobre como criar uma janela principal, consulte [instanciando o editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md).  
  
 Uma janela de código é um <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> objeto que tem uma exibição de texto e quaisquer adornos no objeto. Quando você cria a janela de código durante a instanciação do editor principal, o serviço de linguagem pode anexar um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> à janela de código, como é mostrado na ilustração a seguir.  
  
 ![Gráfico de CodeWindow](../extensibility/media/vscodewindow.gif "vscodewindow")  
Janela de código  
  
 O serviço de linguagem implementa o Gerenciador de janelas de código e é responsável por gerenciar adornos, como uma barra suspensa. A janela de código chama o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> método durante a inicialização da janela de código. Quando essa chamada é feita, o serviço de idioma pode adicionar uma barra suspensa ou uma barra de botões ( <xref:Microsoft.VisualStudio.TextManager.Interop.IVsButtonBarClient> ) à janela de código.  
  
## <a name="in-this-section"></a>Nesta seção  
 `Customizing Code Windows by Using the Legacy API`  
 Explica como personalizar janelas de código usando a API herdada.  
  
 [Como hospedar um editor em outro editor](../extensibility/how-to-host-an-editor-in-another-editor.md)  
 Explica como hospedar um segundo editor dentro de uma janela do editor.  
  
 [Como disparar eventos quando o editor perde o foco](../extensibility/how-to-fire-events-when-the-editor-loses-focus.md)  
 Explica como anexar uma exibição de documento a um objeto de dados de documento.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsCodeWindow>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer>   
 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>   
 [Criando uma instância do editor principal usando a API herdada](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)   
 [Acessando a exibição de texto usando a API herdada](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
