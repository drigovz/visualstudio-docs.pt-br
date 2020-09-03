---
title: Acessando a exibição de texto usando a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text view
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f9396e4523e38e7313efb5668c4680f551558ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184942"
---
# <a name="accessing-thetext-view-by-using-the-legacy-api"></a>Acessar a exibição de texto usando a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uma exibição de texto é uma apresentação do texto armazenado em um buffer de texto. Você pode acessar a exibição de texto usando a API herdada, conforme mostrado na seção a seguir.  
  
## <a name="text-view-object"></a>Objeto de exibição de texto  
 Cada exibição é associada a seu próprio buffer de texto e a exibição é uma janela sobre os dados no buffer. O diagrama a seguir mostra as principais interfaces do objeto de exibição de texto, que é representado por <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> .  
  
 ![Objeto de exibição de texto do Visual Studio](../extensibility/media/vstextview.gif "vstextview")  
Objeto de exibição de texto  
  
 A exibição é uma maneira de apresentar o texto no buffer. Ele inclui recursos como quebra automática de palavras e estrutura de tópicos para que o que você vê na exibição não seja uma representação exata do texto no buffer.  
  
 Uma exibição permite que outros serviços ou processos interceptem comandos de entrada e atuem neles antes que a exibição atue neles. O serviço mais comum para fazer isso é um serviço de linguagem. Um serviço de linguagem pode precisar, por exemplo, interceptar o comando para a tecla ENTER para fornecer comportamento de recuo personalizado ou dicas de ferramenta.  
  
## <a name="adding-functionality-to-the-text-view"></a>Adicionando funcionalidade à exibição de texto  
 Você pode personalizar o comportamento da exibição de texto manipulando pressionamentos de tecla específicos. Para interceptar os pressionamentos de teclas, você implementa <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> em seu objeto e fornece um destino de comando ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> ) para monitorar e interceptar comandos.  
  
 A exibição de texto usa a arquitetura sequencial para filtros de comando. Novos filtros de comando ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> objetos) são adicionados à sequência chamando o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> método.  
  
 A notificação de eventos para a exibição de texto é fornecida usando a `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents` interface. Implemente essa interface no objeto de cliente para receber a notificação de alterações na exibição de texto. Expor essa interface à exibição de texto usando a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> interface na exibição de texto para receber a notificação de alterações da exibição.  
  
## <a name="see-also"></a>Consulte Também  
 [Alterando as configurações de exibição usando a API herdada](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [Usando o gerenciador de texto para monitorar as configurações globais](../extensibility/using-the-text-manager-to-monitor-global-settings.md)
