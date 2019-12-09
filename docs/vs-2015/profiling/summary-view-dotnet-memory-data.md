---
title: Exibição Resumo – Dados da memória do .NET | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0cb317c3-0ae6-4531-aaa8-447576eec037
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe6d3982828d1e2a8ae4aeaba3d89b1b75f4f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68193325"
---
# <a name="summary-view---net-memory-data"></a>Exibição Resumo – Dados de memória do .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição Resumo exibe informações sobre as funções e os tipos do .NET que alocaram a maior quantidade de memória e os tipos que foram criados mais vezes em uma execução de criação de perfil. Para obter mais informações, incluindo uma descrição das listas Links de notificação e Relatório, consulte [Exibição Resumo](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Gráfico de linha do tempo  
 O gráfico de linha do tempo na exibição Resumo mostra a utilização do processador (CPU) pelo aplicativo com perfil ao longo do tempo em que ocorreu a criação de perfil. É possível usar o gráfico de linha do tempo para filtrar a exibição para um intervalo de tempo selecionado. Para obter mais informações, consulte [Como filtrar exibições de relatório por meio da linha do tempo de resumo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="functions-allocating-most-memory"></a>Funções que Alocam Mais Memória  
 Lista as funções que alocaram o maior número de bytes de memória na execução de criação de perfil.  
  
|Column|DESCRIÇÃO|  
|------------|-----------------|  
|**Nome**|O nome da função.|  
|**% de bytes**|O percentual de todos os bytes alocados na execução de criação de perfil que foram alocados por essa função ou por uma função filho chamada por essa função.|  
  
## <a name="types-with-most-memory-allocated"></a>Tipos com mais memória alocada  
 Lista os tipos para os quais o maior número de bytes de memória foi alocado na execução de criação de perfil.  
  
|Column|DESCRIÇÃO|  
|------------|-----------------|  
|**Nome**|O nome do tipo.|  
|**% de bytes**|O percentual de todos os bytes alocados na execução de criação de perfil que foram alocados para esse tipo.|  
  
## <a name="types-with-most-instances"></a>Tipos com mais instâncias  
 Lista os tipos que foram criados mais vezes durante a execução de criação de perfil. tinha  
  
|Column|DESCRIÇÃO|  
|------------|-----------------|  
|**Nome**|O nome do tipo.|  
|**% de instâncias**|O percentual do número total de objetos do .NET que foram criados na execução de criação de perfil que eram instâncias desse tipo.|  
  
## <a name="see-also"></a>Veja também  
 [Exibição Resumo](../profiling/summary-view-sampling-data.md)   
 [Exibição de Resumo](../profiling/summary-view-instrumentation-data.md)
