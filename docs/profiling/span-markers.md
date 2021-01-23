---
title: Marcadores de período | Microsoft Docs
description: Saiba como um marcador de intervalo representa uma fase significativa de um aplicativo e veja um exemplo que mostra um intervalo no Visualizador de simultaneidade.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.markers.span
ms.assetid: 736b7765-9c71-44d7-85e5-79787d13d91c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 28fb9da2e838a17f5b014c3b1af4fc9ee5ab46d7
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720105"
---
# <a name="span-markers"></a>Marcadores de período
Um marcador de período representa uma fase significativa de um aplicativo. Por exemplo, você pode usar um período para representar um intervalo de tempo durante o qual um item de trabalho específico está sendo processado. Seu comprimento representa a duração da fase de aplicativo correspondente. Esta ilustração mostra um período na Visualização Simultânea:

 ![Um marcador de intervalo no Visualizador de simultaneidade](../profiling/media/cvmarkerspan.png "CVMarkerSpan") Um marcador de intervalo no Visualizador de simultaneidade

## <a name="span-category"></a>Categoria de período
 Um marcador de período pode ser exibido em cinco cores diferentes, dependendo de sua categoria. As cores são repetidas se há mais de cinco categorias. A categoria pode ser qualquer inteiro. Esta ilustração mostra as cinco cores possíveis:

 ![Cinco spans em categorias diferentes](../profiling/media/cvmarkerspancategory.png "CVMarkerSpanCategory") As cores das primeiras cinco categorias de span

## <a name="span-aggregation-markers"></a>Marcadores de agregação de período
 Às vezes, os marcadores de período ocorrem tão próximos uns dos outros na Visualização Simultânea que não podem ser desenhados individualmente. Quando isso ocorre, um *marcador de agregação de período* cinza que representa os períodos subjacentes é mostrado. Quando você posiciona o ponteiro em desses ícones, uma dica de ferramenta exibe o número de períodos subjacentes representados. Para exibir os períodos, amplie. Se você ampliar completamente e ainda obtiver um marcador de agregação de período, você poderá exibir os marcadores de período subjacentes no [Relatório de Marcadores](../profiling/markers-report.md). Esta ilustração mostra um marcador de agregação de período:

 ![Um marcador de intervalo agregado no Visualizador de simultaneidade](../profiling/media/cvmarkerspanaggregate.png "CVMarkerSpanAggregate") Um marcador de agregação de span

## <a name="see-also"></a>Confira também
- [Marcadores do Visualizador de simultaneidade](../profiling/concurrency-visualizer-markers.md)
- [SDK do Visualizador de Simultaneidade](../profiling/concurrency-visualizer-sdk.md)