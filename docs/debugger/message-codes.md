---
title: Códigos de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c09245056bf7e947985bfa55dc9cc4a3a96b8cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62846267"
---
# <a name="message-codes"></a>Códigos de mensagem
Cada linha de mensagem mostrada no [modo de exibição de mensagens](../debugger/messages-view.md) contém um código ' P, ' s, ' ', ' ou ' R '. Esses códigos têm os seguintes significados:

|Código|Significado|
|----------|-------------|
|P|A mensagem foi postada na fila com a função **CreateMessage** . Nenhuma informação está disponível em relação à disposição final da mensagem.|
|S|A mensagem foi enviada com a função **SendMessage** . Isso significa que o remetente não recupera novamente o controle até que o receptor processe e retorne a mensagem. O receptor pode, portanto, passar um valor de retorno de volta para o remetente.|
|s|A mensagem foi enviada, mas a segurança impede o acesso ao valor de retorno.|
|R|Cada ' line ' tem uma linha ' R ' (Return) correspondente que lista o valor de retorno da mensagem. Às vezes, as chamadas de mensagens são aninhadas, o que significa que um manipulador de mensagens envia outra mensagem.|