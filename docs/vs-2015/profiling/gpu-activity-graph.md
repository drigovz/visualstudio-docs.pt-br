---
title: Gráfico de Atividade de GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.cpu.graph.gpu
ms.assetid: d7c769af-95fb-49a3-b5ab-deafecee46fa
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f4546c3be480349f3e2cb36f483fa8711bc2ac49
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434209"
---
# <a name="gpu-activity-graph"></a>Gráfico de atividade de GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O gráfico de Atividade de GPU na Visualização Simultânea exibe o nível de atividade do DirectX no sistema, medido pelo número de mecanismos do DirectX em uso ao longo do tempo.  O gráfico não mostra quais mecanismos específicos foram usados.  É considerado que um mecanismo está em uso se ele estiver processando qualquer trabalho da GPU.  
  
## <a name="gpu-activity-graph-colors"></a>Cores do gráfico de Atividade de GPU  
 Verde indica o consumo de mecanismos do DirectX pelo processo atual.  
  
 Cinza claro indica o consumo de mecanismos do DirectX por outros processos no sistema. Para reduzir o consumo de mecanismos do DirectX por outros processos, reduza o número de outros processos em execução no sistema.  
  
 Branco indica a disponibilidade de mecanismos do DirectX não utilizados no sistema. Esses mecanismos estão disponíveis para seu processo se você puder encontrar mais oportunidades de explorá-los. Alguns mecanismos só podem ser usados para tipos específicos de tarefas.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)
