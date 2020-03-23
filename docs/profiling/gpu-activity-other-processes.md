---
title: Atividade de GPU (outros processos) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.timeline.gpuother
- vs.cv.threads.timeline.gpuactivity
ms.assetid: 8a68df65-eb63-452f-9285-fb4ffc92f2b2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a502590c20fce1455d9259ae681178d9cd48e33
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969496"
---
# <a name="gpu-activity-other-processes"></a>Atividade de GPU (outros processos)
Os segmentos **Atividade de GPU (outros processos)** na exibição Threads na Visualização Simultânea representam o tempo durante o qual a GPU estava processando solicitações em nome de outros processos no sistema. Essas solicitações são enviadas à GPU como pacotes de DMA (acesso direto à memória).  O tamanho de um segmento representa o tempo durante o qual o pacote foi processado pela GPU.

 Quando você seleciona este tipo de segmento, o relatório na guia **Atual** exibe informações sobre o pacote que foi processado.  As informações incluem a quantidade de tempo que o pacote esperou na fila de hardware associada ao mecanismo do DirectX, o processo que enviou o pacote e o tempo necessário para processar o pacote.