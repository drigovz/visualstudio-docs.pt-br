---
title: Atividade de GPU (paginação) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuactivity
- vs.cv.threads.timeline.gpupaging
ms.assetid: 95284ac5-3492-4f7b-a79f-7d2840a07679
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5979ccf8cafedb849b7ae9f7af6b0b35096e624f
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54769077"
---
# <a name="gpu-activity-paging"></a>Atividade de GPU (paginação)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os segmentos de **Atividade de GPU (paginação)** na guia Threads representam o tempo durante o qual a GPU estava processando solicitações de paginação.  O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de paginação de DMA (acesso direto à memória). Normalmente, pacotes de paginação são associados à transferência de memória entre a CPU e a GPU.  
  
 Quando você seleciona um segmento de paginação da GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Isso inclui a quantidade de tempo que ele esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote de DMA e o tempo necessário para processar o pacote.  
  
## <a name="see-also"></a>Consulte também  
 [Exibição da utilização](../profiling/utilization-view.md)
