---
title: Tempo de preempção | Microsoft Docs
description: Saiba mais sobre o Premption tempo e que esses segmentos na linha do tempo estão associados ao tempo de bloqueio Categorizado como preempção.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a102b11fdc7608b94b97105b061e28860f41a9a1
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719507"
---
# <a name="preemption-time"></a>Tempo de preempção
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Preempção. Esta categoria implica que um thread é alternado devido a um destes motivos:

- O agendador substituiu usando um thread de prioridade mais alta.

- O quantum de execução do thread expirou e outros threads estavam prontos para execução.

  Durante esse tempo, um thread foi bloqueado pelo motivo de espera do kernel, que a Visualização Simultânea está contando como preempção. Os segmentos de preempção são iniciados quando um thread é enviado de um núcleo lógico e terminam quando esse thread continua a execução.

  A dica de ferramenta para um segmento de preempção exibe o nome do processo ou do thread que causou a preempção. No entanto, isso não significa que o processo ou thread que assumiu o controle foi realmente executado durante o período de admitiu preempção.

## <a name="see-also"></a>Confira também
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)