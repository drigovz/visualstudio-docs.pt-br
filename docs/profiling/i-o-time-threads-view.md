---
title: Tempo de E-S (Exibição de Threads) | Microsoft Docs
description: Saiba como os segmentos de tempo de e/s são associados a tempos de bloqueio que são categorizados como e/s, o que significa que um thread está aguardando a conclusão de uma operação de e/s.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.io
helpviewer_keywords:
- Concurrency Visualizer, I/O time (Threads View)
ms.assetid: 0c4ec14d-d8dd-49c1-999c-dcbf4e8e1dc8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e147d97616f846339dc12e3941f6944f277d8318
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99906865"
---
# <a name="io-time-threads-view"></a>tempo de E/S (Exibição Threads)
Esses segmentos na linha do tempo estão associados aos tempos de bloqueio categorizados como E/S. Isso significa que um thread está aguardando uma operação de E/S ser concluída. O thread pode ter sido bloqueado em uma API ou por uma espera de kernel relacionado ao Visualizador de Simultaneidade que está contando como E/S. APIs como `CreateFile()`, `ReadFile()` e `WSARecv()` pertencem a esse grupo.

## <a name="see-also"></a>Confira também
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)