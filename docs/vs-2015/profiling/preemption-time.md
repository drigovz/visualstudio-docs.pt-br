---
title: Tempo de preempção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.preemption
helpviewer_keywords:
- Concurrency Visualizer, Preemption Time
ms.assetid: 6b78f91e-a006-440c-83fb-e7368040951d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6fd209f65464126650106eb4509cd3de39ad8c25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198071"
---
# <a name="preemption-time"></a>Tempo de preempção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Preempção. Esta categoria implica que um thread é alternado devido a um destes motivos:  
  
- O agendador substituiu usando um thread de prioridade mais alta.  
  
- O quantum de execução do thread expirou e outros threads estavam prontos para execução.  
  
  Durante esse tempo, um thread foi bloqueado por uma espera de kernel, motivo pelo qual a visualização simultânea está contando como preempção. Segmentos de preempção iniciam quando um thread é empurrado para fora de um núcleo lógico e terminam quando esse thread continua a execução.  
  
  A dica de ferramenta para um segmento que admitiu preempção exibe o nome do processo ou thread que causou a preempção. No entanto, isso não significa que o processo ou thread que assumiu o controle foi realmente executado durante o período de admitiu preempção.  
  
## <a name="see-also"></a>Consulte Também  
 [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)
