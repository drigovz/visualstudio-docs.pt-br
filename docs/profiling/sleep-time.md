---
title: Tempo de Suspensão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be2d566228367e2cdb07aecc2d73eaf82a6d961f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62980207"
---
# <a name="sleep-time"></a>Tempo de suspensão
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Suspensão. A categoria de suspensão indica que um thread voluntariamente cedeu seu núcleo lógico e não está trabalhando. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como suspensão. APIs como `Sleep()` e `SwitchToThread()` pertencem a esse grupo.

## <a name="see-also"></a>Consulte também
- [Exibição de threads](../profiling/threads-view-parallel-performance.md)