---
title: Guia atual | Microsoft Docs
description: Selecione a guia atual da exibição threads para ver uma pilha de chamadas para um segmento de thread de CPU ou um segmento de bloqueio. Também há informações sobre segmentos do DirectX.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.reportnav.current
helpviewer_keywords:
- Concurrency Visualizer, Callstack at Selection Point
ms.assetid: 2c7b1ae5-3756-4795-bc59-f6bb113f2ba5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4125a40ea0be18cceb99e7f3a8118a10d26a5437
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955860"
---
# <a name="current-tab"></a>Guia atual
Ao clicar na guia **Atual**, é possível ver uma pilha de chamadas (se disponível) que está próxima ao ponto de seleção atual na linha do tempo se um segmento de thread da CPU está selecionado.  Nesse caso, o ponto de seleção é representado por uma seta preta ou um cursor, acima da linha do tempo. Quando um segmento de bloqueio é selecionado, o cursor do sistema não é exibido porque não houve nenhuma execução. No entanto, o segmento ainda está realçado e uma pilha de chamadas é exibida.

 A guia **Atual** também exibe informações sobre segmentos de atividade do DirectX, marcadores e acesso de E/S.  Para segmentos de atividade do DirectX, são exibidas informações sobre a forma como os pacotes DMA são processados pela fila de hardware.  Para os marcadores, são exibidas informações sobre a descrição e o tipo de marcador.  Para o acesso de E/S, são exibidas informações sobre o arquivo e o número de bytes lidos ou gravados.

## <a name="see-also"></a>Consulte também
- [Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)