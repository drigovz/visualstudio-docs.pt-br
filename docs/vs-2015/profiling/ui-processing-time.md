---
title: Tempo de processamento de interface do usuário | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bbed9d8c4725b6bd497377d4a9dee22f2f8573d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68145491"
---
# <a name="ui-processing-time"></a>Tempo de processamento de interface do usuário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Processamento de Interface do Usuário. Isso significa que um thread está bombeando mensagens do Windows ou realizando outro trabalho de interface do usuário. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como Processamento de Interface do Usuário. APIs como `GetMessage()` e `MsgWaitForMultipleObjects()` pertencem a esse grupo.  
  
 Se nenhuma API de bloqueio predefinida for identificada, examine as pilhas de chamadas e relatórios de perfil para determinar as causas subjacentes do atraso.  
  
 A categoria de Processamento de Interface do Usuário é importante para compreender a capacidade de resposta dos aplicativos de GUI e é desejável em aplicativos que dependem da capacidade de resposta da interface do usuário. Por exemplo, se o thread de interface do usuário em um aplicativo alcançar 100% de tempo no Processamento de Interface do Usuário, provavelmente, ele terá uma grande capacidade de resposta. No entanto, se o thread de interface do usuário gastar um tempo considerável em outras categorias, procure as causas raiz e considere opções para reduzir categorias sem interface do usuário nesse thread.  
  
## <a name="see-also"></a>Veja também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)
