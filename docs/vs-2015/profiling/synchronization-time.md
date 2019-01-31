---
title: Tempo de sincronização | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.synchronization
helpviewer_keywords:
- Concurrency Visualizer, Synchronization Time
ms.assetid: affa04cc-8bba-4848-9301-b19846d3c2cb
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 218f333f97e8252993f87893238a0f51f964d6c1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790321"
---
# <a name="synchronization-time"></a>Tempo de sincronização
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esses segmentos na linha do tempo estão associados os tempos de bloqueio categorizados como Sincronização. Quando um thread está marcado como bloqueado na sincronização, é sugerida uma dessas coisas:  
  
- A execução do thread pode ter resultado em uma chamada para uma API de sincronização de thread conhecidos como `EnterCriticalSection()` ou `WaitForSingleObject()`.  
  
- O algoritmo de correspondência de API não pode ser totalmente abrangente e, portanto, algumas APIs que podem ser mapeadas para outras categorias também podem aparecer como sincronização, porque um quadro na pilha de chamadas eventualmente atingiu um kernel subjacente bloqueando primitivo que foi mapeado para essa categoria.  
  
  Para entender a causa de um evento de bloqueio de thread, examine cuidadosamente o bloqueio de pilhas de chamadas e os relatórios de perfil.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)
