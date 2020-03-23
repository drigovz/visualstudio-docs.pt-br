---
title: Atividade de GPU (este processo) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuexecution
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 0956edbf-9bcd-4afe-9287-fda628648ca0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 68e85fc44977a3d9756965de12e25d13d62dbb89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969532"
---
# <a name="gpu-activity-this-process"></a>Atividade de GPU (este processo)
Os segmentos **Atividade de GPU (este processo)** na exibição Threads na Visualização Simultânea representam o tempo durante o qual a GPU estava processando solicitações em nome do processo atual. Essas solicitações são enviadas à GPU como pacotes de DMA (acesso direto à memória). O tamanho de um segmento representa o tempo durante o qual a GPU estava processando um pacote de DMA em nome do processo atual.

 Quando você seleciona o segmento de atividade de GPU, o relatório na guia **Atual** exibe informações sobre o pacote de DMA que foi processado. Essas informações incluem a quantidade de tempo que o pacote esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote e o tempo necessário para processar o pacote. Um processo diferente do processo atual pode ter enviado fisicamente o pacote de DMA à GPU. A Visualização Simultânea pode detectar quando outro processo enviou trabalho à GPU em nome do processo atual.