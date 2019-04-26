---
title: Tempo de sincronização | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ae73f7b9a9838a006dce47bf44b0ed46aa0b84fa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62965304"
---
# <a name="synchronization-time"></a>Tempo de sincronização
Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Sincronização. Quando um thread está marcado como bloqueado na sincronização, é sugerida uma dessas coisas:

- A execução do thread pode ter resultado em uma chamada para uma API de sincronização de thread conhecidos como `EnterCriticalSection()` ou `WaitForSingleObject()`.

- O algoritmo de correspondência de API não pode ser totalmente abrangente e, portanto, algumas APIs que podem ser mapeadas para outras categorias também podem aparecer como sincronização, porque um quadro na pilha de chamadas eventualmente atingiu um kernel subjacente bloqueando primitivo que foi mapeado para essa categoria.

  Para entender a causa de um evento de bloqueio de thread, examine cuidadosamente o bloqueio de pilhas de chamadas e os relatórios de perfil.

## <a name="see-also"></a>Consulte também
- [Exibição de threads](../profiling/threads-view-parallel-performance.md)