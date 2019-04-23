---
author: dotpaul
ms.author: paulming
ms.date: 04/05/2019
ms.topic: include
ms.openlocfilehash: 43327901b2233b9b2818296f9269975d8524438b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118143"
---
Desserializadores inseguros estão vulneráveis ao desserializar dados não confiáveis. Um invasor poderia modificar os dados serializados para incluir tipos inesperados com efeito colateral mal-intencionado. Um ataque contra um desserializador inseguro poderia, por exemplo, executar comandos no sistema operacional subjacente, se comunicar pela rede ou excluir arquivos.