---
title: Códigos de mensagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1f568ead3e5862460d4ae4e18e51687737d4a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866290"
---
# <a name="message-codes"></a>Códigos de mensagem
Cada linha da mensagem mostrada na [exibição de mensagens](../debugger/messages-view.md) contém um 'P', do,' do,' ou 'R' código. Esses códigos têm os seguintes significados:  
  
|Código|Significado|  
|----------|-------------|  
|P|A mensagem foi postada na fila com o **PostMessage** função. Nenhuma informação está disponível sobre a ultimate disposição da mensagem.|  
|S|A mensagem foi enviada com o **SendMessage** função. Isso significa que o remetente não recuperar o controle até que o receptor processa e retorna a mensagem. O receptor pode, portanto, passar um valor de retorno volta ao remetente.|  
|s|A mensagem foi enviada, mas segurança impede o acesso ao valor de retorno.|  
|R|De cada um ' linha tem uma linha correspondente 'R' (retorno) que lista o valor de retorno de mensagem. Às vezes chamadas de mensagem são aninhadas, que significa que esse manipulador de uma mensagem envia outra mensagem.|