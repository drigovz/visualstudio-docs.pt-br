---
title: Como registrar eventos de buffer de texto com a API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register for text buffer events
ms.assetid: 5fc00ced-882c-4b48-b46c-1fa5a2469f94
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f36e8dd780788d241e3c286b1bbbe581311b143
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204092"
---
# <a name="how-to-register-for-text-buffer-events-with-the-legacy-api"></a>Como registrar para eventos de buffer de texto com a API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se você estiver acessando o buffer de texto usando a API herdada, deverá se registrar para eventos de buffer de texto, conforme mostrado no procedimento a seguir.  
  
### <a name="to-advise-text-buffer-events"></a>Para avisar eventos de buffer de texto  
  
1. De um ponteiro para uma das interfaces em <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> , chame `QueryInterface` um ponteiro para <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> .  
  
2. Chame o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer.FindConnectionPoint%2A> método e passe a ID da interface dos eventos que você deseja registrar.  
  
     Por exemplo, se você quiser se registrar para o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> , passe uma ID de interface de IID_IVsTextLinesEvents.  
  
     O buffer de texto retorna um ponteiro para a <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interface do objeto de ponto de conexão apropriado.  
  
3. Usando esse ponteiro, chame o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> método, passando um ponteiro para a implementação da interface de eventos para a qual você deseja se registrar, por exemplo, a `IVsTextLinesEvents` interface.  
  
     O ambiente retorna um cookie que você pode usar para parar de escutar eventos chamando o <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Unadvise%2A> método.  
  
## <a name="see-also"></a>Consulte Também  
 [Eventos de buffer de texto na API herdada](../extensibility/text-buffer-events-in-the-legacy-api.md)
