---
title: Exibição de núcleos | Microsoft Docs
description: Saiba mais sobre as informações fornecidas pela exibição de núcleos. Ele pode ajudá-lo a usar a afinidade de thread ou o gerenciamento de pool de threads para otimizar o desempenho do cache.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.view.cores
helpviewer_keywords:
- Concurrency Visualizer, Cores View
ms.assetid: e47af672-9785-4899-bd45-4d9dda3c396f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4f04fd5021e0ac11cd04e2e04df96da19af1c77
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951661"
---
# <a name="cores-view"></a>Exibição de núcleos
A **Exibição de Núcleos** mostra como a execução do thread foi mapeada para os núcleos de processador lógico (escolha **Analisar** > **Visualizador de Simultaneidade** para iniciar o visualizador de simultaneidade). Se você estiver escrevendo aplicativos de servidor, essa exibição poderá ajudá-lo a otimizar o desempenho de cache usando o gerenciamento do pool de threads ou a afinidade de thread. Ela também pode ajudá-lo a examinar os casos em que o uso da afinidade de thread pode ter piorado o problema da migração de núcleo cruzado. A Exibição de Núcleos tem duas partes: um grafo e uma legenda.

 O gráfico mostra os núcleos lógicos no eixo Y e o tempo no eixo X. Cada thread no gráfico tem uma cor exclusiva para que seja possível acompanhar seu movimento entre os núcleos ao longo do tempo. É possível filtrar os threads nesse gráfico selecionando-os na área de legenda.

 A área de legenda tem uma entrada para cada cor no gráfico. Cada entrada mostra a cor e o nome do thread, o número de alternâncias de contexto de núcleo cruzado, o número total de alternâncias de contexto e o percentual de alternâncias de contexto que cruzam núcleos. A legenda é classificada pelo número de alternâncias de contexto de núcleo cruzado, em ordem decrescente. Ela lista apenas os threads executados durante o intervalo de tempo exibido.  A lista será atualizada se você aplicar zoom ou movimento panorâmico.

## <a name="see-also"></a>Consulte também
- [Visualizador de Simultaneidade](../profiling/concurrency-visualizer.md)
- [Exibição da utilização](../profiling/utilization-view.md)
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)