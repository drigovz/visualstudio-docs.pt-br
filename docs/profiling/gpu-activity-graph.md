---
title: Gráfico de Atividade de GPU | Microsoft Docs
description: Entenda o grafo atividade de GPU, que é exibido no Visualizador de simultaneidade o nível de atividade do DirectX no sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bccf4869a1197306017b443b00670cc123300a48
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801321"
---
# <a name="gpu-activity-graph"></a>Gráfico de atividade de GPU
O gráfico de Atividade de GPU na Visualização Simultânea exibe o nível de atividade do DirectX no sistema, medido pelo número de mecanismos do DirectX em uso ao longo do tempo.  O gráfico não mostra quais mecanismos específicos foram usados.  É considerado que um mecanismo está em uso se ele estiver processando qualquer trabalho da GPU.

## <a name="gpu-activity-graph-colors"></a>Cores do gráfico de atividade de GPU
 Verde indica o consumo de mecanismos do DirectX pelo processo atual.

 Cinza claro indica o consumo de mecanismos do DirectX por outros processos no sistema. Para reduzir o consumo de mecanismos do DirectX por outros processos, reduza o número de outros processos em execução no sistema.

 Branco indica a disponibilidade de mecanismos do DirectX não utilizados no sistema. Esses mecanismos estão disponíveis para seu processo se você puder encontrar mais oportunidades de explorá-los. Alguns mecanismos só podem ser usados para tipos específicos de tarefas.

## <a name="see-also"></a>Confira também
- [Exibição da utilização](../profiling/utilization-view.md)