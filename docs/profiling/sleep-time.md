---
title: Tempo de Suspensão | Microsoft Docs
description: Saiba que a categoria de suspensão implica que um thread tenha dado voluntariamente seu núcleo lógico e não está funcionando.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.sleep
helpviewer_keywords:
- Concurrency Visualizer, Sleep Time
ms.assetid: 3ddb96f9-9bda-4a68-ad4d-ef488a0a68dc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a433d11c2684a4a39660759f33d49bd719c2b2ae
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960163"
---
# <a name="sleep-time"></a>Tempo de suspensão
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Suspensão. A categoria de suspensão indica que um thread voluntariamente cedeu seu núcleo lógico e não está trabalhando. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como suspensão. APIs como `Sleep()` e `SwitchToThread()` pertencem a esse grupo.

## <a name="see-also"></a>Confira também
- [Exibição de threads](../profiling/threads-view-parallel-performance.md)