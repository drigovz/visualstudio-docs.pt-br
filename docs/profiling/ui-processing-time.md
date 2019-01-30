---
title: Tempo de processamento de interface do usuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: be698fdb7dd931b4609e797434116d2eb1b5056e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54940031"
---
# <a name="ui-processing-time"></a>Tempo de processamento de interface do usuário
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Processamento de Interface do Usuário. Isso significa que um thread está bombeando mensagens do Windows ou realizando outro trabalho de interface do usuário. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como Processamento de Interface do Usuário. APIs como `GetMessage()` e `MsgWaitForMultipleObjects()` pertencem a esse grupo.  
  
 Se nenhuma API de bloqueio predefinida for identificada, examine as pilhas de chamadas e relatórios de perfil para determinar as causas subjacentes do atraso.  
  
 A categoria de Processamento de Interface do Usuário ajuda você a compreender a capacidade de resposta dos aplicativos de GUI e é desejável em aplicativos que dependem da capacidade de resposta da interface do usuário. Por exemplo, se o thread de interface do usuário em um aplicativo alcançar 100% de tempo no Processamento de Interface do Usuário, provavelmente, ele terá uma boa capacidade de resposta. No entanto, se o thread de interface do usuário gastar um tempo considerável em outras categorias, procure as causas raiz e considere opções para reduzir categorias sem interface do usuário nesse thread.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição de Threads](../profiling/threads-view-parallel-performance.md)