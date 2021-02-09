---
title: Códigos de mensagem | Microsoft Docs
description: Conheça os significados dos códigos de mensagem mostrados em cada linha de mensagem da exibição de mensagens.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 92562dda3e8a705d2cdf9b00561aa13cbd9d75e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891768"
---
# <a name="message-codes"></a>Códigos de mensagem
Cada linha de mensagem mostrada no [modo de exibição de mensagens](../debugger/messages-view.md) contém um código ' P, ' s, ' ', ' ou ' R '. Esses códigos têm os seguintes significados:

|Código|Significado|
|----------|-------------|
|P|A mensagem foi postada na fila com a função **CreateMessage** . Nenhuma informação está disponível em relação à disposição final da mensagem.|
|S|A mensagem foi enviada com a função **SendMessage** . Isso significa que o remetente não recupera novamente o controle até que o receptor processe e retorne a mensagem. O receptor pode, portanto, passar um valor de retorno de volta para o remetente.|
|s|A mensagem foi enviada, mas a segurança impede o acesso ao valor de retorno.|
|R|Cada ' line ' tem uma linha ' R ' (Return) correspondente que lista o valor de retorno da mensagem. Às vezes, as chamadas de mensagens são aninhadas, o que significa que um manipulador de mensagens envia outra mensagem.|