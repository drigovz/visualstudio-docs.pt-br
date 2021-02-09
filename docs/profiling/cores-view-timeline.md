---
title: Linha do tempo da exibição de núcleos | Microsoft Docs
description: 'Aprenda as noções básicas da linha do tempo: como determinar qual thread foi executado em qual núcleo em qualquer momento e como ampliar e reduzir.'
custom.ms: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cores.timeline.threads
helpviewer_keywords:
- Concurrency Visualizer, Cores View Timeline
ms.assetid: 10f0c666-ac2f-4ac5-9fb5-a88f660ab840
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: de09394bfc071cbe3dd1fedad52d1e5a511b62c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882889"
---
# <a name="cores-view-timeline"></a>Linha do tempo da exibição de núcleos
Cada linha na linha do tempo representa um núcleo de processador lógico no sistema com perfil sendo criado. Para cada linha, o eixo horizontal mostra qual thread estava sendo executado em um núcleo lógico em um determinado ponto no tempo. É possível focalizar em uma cor de interesse em uma linha do tempo para retornar uma dica de ferramenta que identifica o thread. Para ajudar na identificação do thread, a legenda na parte inferior da janela mostra o que cada cor representa. Use a ferramenta Zoom para ampliar e reduzir, clicando e arrastando ou pressionando CTRL e movendo a roda do mouse. A consistência de zoom é mantida ao mudar entre a Exibição de Núcleos e Exibição de Threads.

## <a name="see-also"></a>Confira também
- [Exibição de núcleos](../profiling/cores-view.md)
- [Controle de zoom (exibição de threads)](../profiling/zoom-control-threads-view.md)