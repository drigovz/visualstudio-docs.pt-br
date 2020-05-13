---
title: Descrições de eventos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], events
ms.assetid: 09f61652-7e16-4bb0-8055-f61a84bf384e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3c2582717fd4da3b833da90a951f9b8f72a59f71
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738791"
---
# <a name="event-descriptions"></a>Descrições de eventos
Cada tipo de evento tem um propósito específico.

## <a name="events-and-the-reasons-for-their-use"></a>Eventos e as razões para seu uso

|Evento|Descrição|
|-----------|-----------------|
|Ativar eventos de documentos|Ocorra quando o motor de depuração (DE) deseja que o IDE abra ou leve um documento para o primeiro plano.|
|Eventos de erro de ponto de ruptura ou de ponto de ruptura|Enviado quando um ponto de ruptura está vinculado ou quando um ponto de ruptura não pode vincular e um erro é retornado.|
|Eventos desvinculados de breakpoint|Ocorre quando um ponto de ruptura vinculado se desvincula do código.|
|Pode parar eventos|Enviado ao IDE para determinar se o usuário gostaria de parar em um ponto especificado no código.|
|Eventos de breakpoint|Ocorre quando um ponto de ruptura de código ou de dados é atingido.|
|Eventos de texto de documento|Ocorre quando o texto em um documento é alterado. Esses eventos não são `IDebugEventCallBack2::Event` enviados através do método.|
|Eventos de criação de motores|Enviado quando um motor é criado pela primeira vez.|
|Eventos de ponto de entrada|Enviado quando o programa está sendo depurado executou seu código de inicialização e atingiu seu primeiro ponto de entrada do usuário.|
|Eventos de exceção|Enviado quando um programa em execução atinge uma exceção.|
|Avaliação de expressões eventos completos|Enviado quando a avaliação de expressão assíncrona estiver completa.|
|Encontrar eventos de símbolo|Enviado sempre que o DE precisa pedir ao usuário para encontrar símbolos para um módulo.|
|Carregar eventos completos|Enviado somente quando a carga inicial do programa estiver concluída e o primeiro código estiver prestes a ser executado no programa.|
|Eventos de mensagens|Enviado quando as mensagens são enviadas aos usuários.|
|Eventos de carga de módulo|Enviado quando um novo módulo é carregado ou descarregado.|
|Eventos de cadeia de saída|Enviado quando o programa grava saída de depuração.|
|Criar e destruir eventos|Enviado para anunciar a criação ou destruição de processos, programas, propriedades, sessões e threads para que o Visual Studio IDE possa acompanhar o estado dos programas que estão sendo depurados.|
|Eventos completos da etapa|Enviado quando um passo está completo.|
|Eventos de alteração de nome do segmento|Enviado quando o usuário altera o nome de um segmento.|
|Eventos de alteração de nome do programa|Enviado quando o usuário altera o nome de um programa.|

## <a name="see-also"></a>Confira também
- [Enviando eventos](../../extensibility/debugger/sending-events.md)
