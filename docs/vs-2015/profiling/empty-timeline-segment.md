---
title: Segmento da linha do tempo vazio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.empty
helpviewer_keywords:
- Concurrency Visualizer, empty timeline segment
ms.assetid: f37b301f-3edc-4e56-8084-feec2dc5a9b1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0291cfe93492c357401ce371d58683c6815aa12b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60052812"
---
# <a name="empty-timeline-segment"></a>Segmento da linha de tempo vazio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na Visualização Simultânea, o motivo pelo qual uma seção da linha do tempo está vazia (tem uma tela de fundo branca) depende do tipo de canal.  
  
- Para um canal de thread de CPU, isso significa que o thread não existia durante esta parte da linha do tempo. Se estiver interessado no thread, você poderá encontrar sua seção de execução usando o controle de aplicação de zoom ou rolando horizontalmente.  
  
- Para um canal de E/S, significa que nenhum acesso ao disco ocorreu em nome do processo de destino no momento.  
  
- Para um canal do DirectX, significa que nenhum trabalho de GPU foi executado em nome do processo de destino durante esta parte da linha do tempo.  
  
- Para um canal de marcador, significa que nenhum marcador foi gerado.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição Threads](../profiling/threads-view-parallel-performance.md)   
 [Controle de zoom (exibição de Threads)](../profiling/zoom-control-threads-view.md)
