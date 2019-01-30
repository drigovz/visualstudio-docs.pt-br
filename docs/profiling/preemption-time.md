---
title: Tempo de preempção | Microsoft Docs
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
ms.openlocfilehash: d0e3c3488c54477a9517263bf363cede3198fc3f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55007627"
---
# <a name="preemption-time"></a>Tempo de preempção
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Preempção. Esta categoria implica que um thread é alternado devido a um destes motivos:  
  
- O agendador substituiu usando um thread de prioridade mais alta.  
  
- O quantum de execução do thread expirou e outros threads estavam prontos para execução.  
  
  Durante esse tempo, um thread foi bloqueado pelo motivo de espera do kernel, que a Visualização Simultânea está contando como preempção. Os segmentos de preempção são iniciados quando um thread é enviado de um núcleo lógico e terminam quando esse thread continua a execução.  
  
  A dica de ferramenta para um segmento de preempção exibe o nome do processo ou do thread que causou a preempção. No entanto, isso não significa que o processo ou thread que assumiu o controle foi realmente executado durante o período de admitiu preempção.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)