---
title: Gráfico de utilização da CPU | Microsoft Docs
description: Saiba mais sobre o grafo de utilização da CPU, que mostra o nível de utilização em um aplicativo ao longo do tempo. A utilização é mostrada como o número de núcleos lógicos em uso.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph
helpviewer_keywords:
- CPU Utilization GraphConcurrency Visualizer, CPU Utilization Graph
ms.assetid: 5332fd38-622d-47a3-874f-8c2fd7a30f95
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5ec57ac6601557bf644c818822fea70a296fd0c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956003"
---
# <a name="cpu-utilization-graph"></a>Grafo de utilização da CPU
O gráfico de Utilização da CPU mostra o nível de utilização em um aplicativo ao longo do tempo. O eixo X representa a duração do rastreamento e o eixo Y representa o número de núcleos lógicos no sistema. O gráfico não mostra qual núcleo específico está ativo em determinado momento. Por exemplo, se dois núcleos estiverem sendo executados individualmente com capacidade de 50% durante um período específico, essa exibição mostrará um núcleo lógico sendo utilizado.

## <a name="cpu-utilization-graph-colors"></a>Cores do gráfico de Utilização da CPU

- Verde indica a utilização dos núcleos lógicos no sistema pelo processo atual.

- Cinza-claro indica a utilização de núcleos lógicos por outros processos no sistema. Um alto percentual de cinza claro no grafo de CPU indica que o sistema está muito carregado por outros processos e que seu processo provavelmente será admitido por eles. Para reduzir o consumo de núcleos lógicos por outros processos, reduza o número deles em execução no sistema.

- Cinza-escuro indica o consumo de núcleos lógicos pelo processo do sistema. Não é possível controlar isso diretamente, mas é útil saber quando isso está ocorrendo, pois pode afetar a disponibilidade de núcleos lógicos para o processo.

- Branco indica a disponibilidade de núcleos lógicos não utilizados no sistema. Esses núcleos estarão disponíveis para o processo se você puder encontrar mais oportunidades de paralelismo.

## <a name="see-also"></a>Confira também
- [Exibição da utilização](../profiling/utilization-view.md)
- [Utilização da CPU média](../profiling/average-cpu-utilization.md)