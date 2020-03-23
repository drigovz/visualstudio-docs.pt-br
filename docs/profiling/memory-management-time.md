---
title: Tempo de gerenciamento da memória | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.paging
helpviewer_keywords:
- Concurrency Visualizer, Paging Time
ms.assetid: 67af3509-3a7d-435d-bc37-5262448da915
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 442973edb18e75bafda8a9397eac799286c69dfa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62963775"
---
# <a name="memory-management-time"></a>Tempo de gerenciamento de memória
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Gerenciamento da Memória. Esse cenário significa que um thread está bloqueado por um evento associado a uma operação de gerenciamento de memória, como paginação. Durante esse tempo, um thread foi bloqueado em um estado de API ou kernel que a Visualização Simultânea está contando como gerenciamento de memória. Eles incluem eventos como paginação e alocação de memória.

 Examine os relatórios de perfil e as pilhas de chamada associados para entender melhor os motivos subjacentes para os bloqueios categorizados como Gerenciamento de Memória.

## <a name="see-also"></a>Confira também
- [Exibição de linhas](../profiling/threads-view-parallel-performance.md)