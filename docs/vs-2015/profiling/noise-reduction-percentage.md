---
title: Percentual de redução do ruído | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c6407b40f58c3acc02705379768085793a2b79b6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195549"
---
# <a name="noise-reduction-percentage"></a>Porcentagem de redução do ruído
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Por padrão, o valor da configuração de Percentual de Redução do Ruído é 2. Somente as entradas que têm um percentual de tempo inclusivo maior ou igual a essa configuração são mostradas na árvore de chamadas. Ao alterar a configuração, é possível controlar a quantidade de entradas mostradas na árvore de chamadas. Por exemplo, alterar o valor para 10 mostrará apenas as entradas da árvore chamada que têm um tempo inclusivo maior ou igual a 10%. Ao aumentar o valor da configuração, é possível se concentrar em entradas que têm maior impacto sobre o desempenho do processo.
