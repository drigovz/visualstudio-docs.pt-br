---
title: Envio de eventos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], sending events
ms.assetid: 064231e7-59b5-4437-8240-a23c0a7ec2a9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd282dd38d322a5b7d9821406d30a303fabb02bb
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685060"
---
# <a name="send-events"></a>Enviar eventos
O mecanismo de comunicação entre o depurador e o mecanismo de depuração (DES) é um modelo de evento com base no DCOM. Os eventos são enviados como objetos COM, e cada evento tem parâmetros que especificam:

- O DE que o evento de chamada.

- Uma descrição do que aconteceu.

- O processo, programa e informações de thread que identifica o contexto de onde o evento ocorreu. O processo não é enviado para eventos enviados a partir DE.

- O tipo de evento que indica se o evento é síncrona ou assíncrona.

  Todos os eventos de depuração são enviados usando o método [IDebugEventCallback2::Event](../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="in-this-section"></a>Nesta seção
 [Fontes de evento](../../extensibility/debugger/event-sources-visual-studio-sdk.md) explica as duas fontes de eventos: o mecanismo de depuração (DE) e a sessão de depuração do SDM (Gerenciador).

 [Suporte para tipos de evento](../../extensibility/debugger/supported-event-types.md) discute os tipos de eventos com suporte no momento: síncrono e assíncrono.

 [Descrições de eventos](../../extensibility/debugger/event-descriptions.md) define eventos e os motivos para seu uso.

## <a name="related-sections"></a>Seções relacionadas
 [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md) descreve como a DE funciona com o sistema operacional ou interpretador para fornecer serviços de depuração.