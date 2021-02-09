---
title: Tempo de processamento de interface do usuário | Microsoft Docs
description: Saiba que os segmentos na linha do tempo estão associados a tempos de bloqueio categorizados como processamento da interface do usuário.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.uiprocessing
helpviewer_keywords:
- Concurrency Visualizer, UI Processing Time
ms.assetid: 0ddb05a3-8c6b-448b-8488-2751c1e5abcc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 809af327fc2bb608647a76575736bd0e2b00c5b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99922029"
---
# <a name="ui-processing-time"></a>Tempo de processamento de interface do usuário
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como Processamento de Interface do Usuário. Isso significa que um thread está bombeando mensagens do Windows ou realizando outro trabalho de interface do usuário. Durante esse tempo, um thread foi bloqueado em uma API que a Visualização Simultânea está contando como Processamento de Interface do Usuário. APIs como `GetMessage()` e `MsgWaitForMultipleObjects()` pertencem a esse grupo.

 Se nenhuma API de bloqueio predefinida for identificada, examine as pilhas de chamadas e relatórios de perfil para determinar as causas subjacentes do atraso.

 A categoria de Processamento de Interface do Usuário ajuda você a compreender a capacidade de resposta dos aplicativos de GUI e é desejável em aplicativos que dependem da capacidade de resposta da interface do usuário. Por exemplo, se o thread de interface do usuário em um aplicativo alcançar 100% de tempo no Processamento de Interface do Usuário, provavelmente, ele terá uma boa capacidade de resposta. No entanto, se o thread de interface do usuário gastar um tempo considerável em outras categorias, procure as causas raiz e considere opções para reduzir categorias sem interface do usuário nesse thread.

## <a name="see-also"></a>Confira também
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)