---
title: Enviando eventos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98247b894d2db628d508713875ba0ea7d0642729
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204734"
---
# <a name="sending-events"></a>Enviando eventos
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O mecanismo de comunicação entre o depurador e o mecanismo DE depuração (DE) é um modelo de evento baseado no DCOM. Os eventos são enviados como objetos COM e cada evento tem parâmetros que especificam o seguinte:  
  
- O que chamou o evento.  
  
- Uma descrição do que aconteceu.  
  
- As informações de processo, programa e thread que identificam o contexto de onde o evento ocorreu. O processo não é enviado para eventos enviados de um DE.  
  
- O tipo de evento que indica se o evento é síncrono ou assíncrono.  
  
  Todos os eventos de depuração são enviados usando o método [IDebugEventCallback2:: Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Origens do evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md)  
 Explica as duas fontes de eventos: o mecanismo de depuração (DE) e o SDM (Gerenciador de depuração de sessão).  
  
 [Tipos de eventos com suporte](../../extensibility/debugger/supported-event-types.md)  
 Discute os tipos de evento com suporte no momento: assíncrono e síncrono.  
  
 [Descrição do evento](../../extensibility/debugger/event-descriptions.md)  
 Define eventos e os motivos para seu uso.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Criar um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
 Descreve como um DE funciona com o interpretador ou o sistema operacional para fornecer serviços de depuração.
