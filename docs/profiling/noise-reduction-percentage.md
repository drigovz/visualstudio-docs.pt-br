---
title: Percentual de redução do ruído | Microsoft Docs
description: Saiba mais sobre a configuração percentual de redução de ruído e como você pode controlar o número de entradas exibidas na árvore de chamadas.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 531ff082197ca1f7e63008aeda1c27e083b569de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922424"
---
# <a name="noise-reduction-percentage"></a>Porcentagem de redução do ruído
Por padrão, o valor da configuração de Percentual de Redução do Ruído é 2. Somente as entradas que têm um percentual de tempo inclusivo maior ou igual a essa configuração são mostradas na árvore de chamadas. Ao alterar a configuração, é possível controlar a quantidade de entradas mostradas na árvore de chamadas. Por exemplo, alterar o valor para 10 mostrará apenas as entradas da árvore chamada que têm um tempo inclusivo maior ou igual a 10%. Ao aumentar o valor da configuração, é possível se concentrar em entradas que têm maior impacto sobre o desempenho do processo.