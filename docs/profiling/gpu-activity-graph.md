---
title: Gráfico de Atividade de GPU | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c274bc5c98a856e5d2f921f2967d8ee474f06274
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53833307"
---
# <a name="gpu-activity-graph"></a>Gráfico de atividade de GPU
O gráfico de Atividade de GPU na Visualização Simultânea exibe o nível de atividade do DirectX no sistema, medido pelo número de mecanismos do DirectX em uso ao longo do tempo.  O gráfico não mostra quais mecanismos específicos foram usados.  É considerado que um mecanismo está em uso se ele estiver processando qualquer trabalho da GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Cores do gráfico de atividade de GPU  
 Verde indica o consumo de mecanismos do DirectX pelo processo atual.  
  
 Cinza claro indica o consumo de mecanismos do DirectX por outros processos no sistema. Para reduzir o consumo de mecanismos do DirectX por outros processos, reduza o número de outros processos em execução no sistema.  
  
 Branco indica a disponibilidade de mecanismos do DirectX não utilizados no sistema. Esses mecanismos estão disponíveis para seu processo se você puder encontrar mais oportunidades de explorá-los. Alguns mecanismos só podem ser usados para tipos específicos de tarefas.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)