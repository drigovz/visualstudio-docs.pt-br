---
title: 'Como: acionar eventos quando o editor perde o foco | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - fire events on losing focus
ms.assetid: 64d40695-6917-468a-8037-a253453ac159
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2ebca733798636ca32787b88b8874c31a2ffffdb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204202"
---
# <a name="how-to-fire-events-when-the-editor-loses-focus"></a>Como disparar eventos quando o editor perde o foco
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Às vezes, é necessário saber quando um editor perde o foco no quadro da janela. Por exemplo, talvez seja necessário extrair o código de uma janela de código depois que o editor não estiver mais focalizado nele. O procedimento a seguir fornece as etapas a serem seguidas para receber a notificação do foco da perda do editor.  
  
### <a name="to-fire-an-event-in-response-to-an-editor-losing-focus"></a>Para acionar um evento em resposta a um editor que está perdendo o foco  
  
1. Monitore eventos de seleção obtendo um <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> objeto de <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> .  
  
2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.AdviseSelectionEvents%2A> e forneça a ele o seu <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents> objeto.  
  
3. Em sua chamada para <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> , procure `elementid==SEID_WindowFrame` .  
  
4. Teste o `varValueNew` parâmetro para duas coisas:  
  
    1. O quadro de janela que você está procurando.  
  
    2. O ponto em que o programa perde a seleção para esse quadro de janela.
