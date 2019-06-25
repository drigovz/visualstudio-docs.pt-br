---
title: Atividade de GPU (este processo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b616e307b3c42b09662be3fdad290ea9f740637c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62434144"
---
# <a name="gpu-activity-this-process"></a>Atividade de GPU (este processo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os segmentos **Atividade de GPU (este processo)** na exibição Threads na Visualização Simultânea representam o tempo durante o qual a GPU estava processando solicitações em nome do processo atual. Essas solicitações são enviadas à GPU como pacotes de DMA (acesso direto à memória). O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de DMA em nome do processo atual.  
  
 Quando você seleciona o segmento de atividade de GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Essas informações incluem a quantidade de tempo que o pacote esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote e o tempo necessário para processar o pacote. Um processo diferente do processo atual pode ter enviado fisicamente o pacote de DMA à GPU. A Visualização Simultânea pode detectar quando outro processo enviou trabalho à GPU em nome do processo atual.
