---
title: Eventos de buffer de texto na API herdada | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffer events
ms.assetid: 9be49e9f-1864-41c2-8a3c-f66895881341
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e82fa31ca435d0c850a4d9e75e927cff9613b046
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186411"
---
# <a name="text-buffer-events-in-the-legacy-api"></a>Eventos de buffer de texto na API herdada
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O objeto buffer de texto emite vários eventos diferentes que permitem que você responda a situações diferentes.  
  
 Ao usar a API herdada, você deve implementar as seguintes interfaces para receber a notificação de alterações no buffer de texto. Expor as interfaces para o buffer de texto usando a `IConnectionPointContainer` interface no buffer de texto para receber a notificação de alterações de linha do buffer. Para obter mais informações, consulte [como registrar eventos de buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md). No caso de `IVsTextStreamEvents` interfaces ou `IVsTextLinesEvents` , as alterações são retornadas em coordenadas de uma ou duas dimensões, respectivamente.  
  
## <a name="text-buffer-interfaces"></a>Interfaces de buffer de texto  
 A seguir estão as interfaces implementadas pelo objeto buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Habilita a criação de ações compostas (ou seja, ações agrupadas em uma única unidade de desfazer/refazer).|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData>|Habilita a persistência de dados de documento gerenciados pelo buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>|Fornece serviços básicos; usado por muitos clientes.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>|Fornece recursos de leitura e gravação usando coordenadas bidimensionais. Herdada de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextScanner>|Fornece acesso seqüencial rápido, orientado a fluxo, ao texto no buffer.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>|Fornece recursos de leitura e gravação usando coordenadas unidimensionais. Herdada de `IVsTextBuffer`.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserData>|Fornece acesso a uma coleção genérica de propriedades. A propriedade mais importante é o nome, ou moniker, do buffer. Você pode armazenar seus próprios dados aleatórios no buffer com essa interface criando um GUID e usando-o como uma chave.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>|Dá suporte a pontos de conexão para eventos.|  
  
## <a name="text-buffer-event-interfaces"></a>Interfaces de evento de buffer de texto  
 A seguir estão as interfaces para notificação de eventos de buffer de texto.  
  
|Interface|Descrição|  
|---------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferEvents>|Notifica os clientes quando um novo serviço de linguagem está associado a um buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferDataEvents>|Notifica os clientes quando um buffer de texto é inicializado e quando são feitas alterações nos dados no buffer de texto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamEvents>|Notifica os clientes sobre as alterações no buffer de texto subjacente em coordenadas unidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents>|Notifica os clientes sobre as alterações no buffer de texto subjacente em coordenadas bidimensionais.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsUserDataEvents>|Notifica os clientes sobre alterações nos dados do usuário.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsPreliminaryTextChangeCommitEvents>|Notifica os clientes sobre o último gesto de confirmação para disparar o evento e fornece o intervalo de texto alterado. A `IVsPreliminaryTextChangeCommitEvents` interface não é acionada em resposta a comandos Undo ou Redo. Os eventos são acionados somente para buffers que têm um Gerenciador de desfazer. `IVsPreliminaryTextChangeCommitEvents` é acionado antes de outros eventos, como uma lista de formatação, para garantir que os outros eventos não alterem o texto antes que as alterações sejam confirmadas. Seu VSPackage deve monitorar a `IVsPreliminaryTextChangeCommitEvents` interface ou a `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsFinalTextChangeCommitEvents>|Notifica os clientes sobre o último gesto de confirmação para disparar o evento e fornece o intervalo de texto alterado. A `IVsFinalTextChangeCommitEvents` interface não é acionada em resposta a comandos Undo ou Redo. Os eventos são acionados somente para buffers que têm um Gerenciador de desfazer. `IVsFinalTextChangeCommitEvents` o destina-se a uso somente por serviços de linguagem ou outros objetos que tenham controle total sobre a edição. Seu VSPackage deve monitorar a `IVsPreliminaryTextChangeCommitEvents` interface ou a `IVsFinalTextChangeCommitEvents` interface, mas não ambos.|  
  
## <a name="see-also"></a>Consulte Também  
 [Acessando o buffer de texto usando a API herdada](../extensibility/accessing-the-text-buffer-by-using-the-legacy-api.md)   
 [Como registrar para eventos de buffer de texto com a API herdada](../extensibility/how-to-register-for-text-buffer-events-with-the-legacy-api.md)
