---
title: Exibição Resumo – Dados de instrumentação | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Summary view
ms.assetid: 0a3b3a1f-e22b-4ac8-b46e-71694e9b2cf1
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc0b4195d33a7bf72d17681b6d71e78f1bacfe5
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157772"
---
# <a name="summary-view---instrumentation-data"></a>Exibição Resumo – Dados de instrumentação
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição Resumo exibe informações sobre as funções mais caras de desempenho em uma execução da criação de perfil. Para obter mais informações, incluindo uma descrição das listas Links de notificação e Relatório, consulte [Exibição Resumo](../profiling/summary-view.md).  
  
## <a name="timeline-graph"></a>Gráfico de linha do tempo  
 O gráfico de linha do tempo na exibição Resumo mostra a utilização do processador (CPU) pelo aplicativo com perfil ao longo do tempo em que ocorreu a criação de perfil. É possível usar o gráfico de linha do tempo para filtrar a exibição para um intervalo de tempo selecionado. Para obter mais informações, consulte [Como filtrar exibições de relatório por meio da linha do tempo de resumo](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Afunilamento  
 O **Afunilamento** exibe o caminho de execução que consumiu mais tempo. É possível clicar em uma função para mostrar a exibição Detalhes da Função referente a ela. Para exibir outras exibições da função, clique com o botão direito do mouse na função e, em seguida, clique em uma exibição na lista.  
  
 O **Afunilamento** inclui os seguintes dados para cada função:  
  
|Column|DESCRIÇÃO|  
|------------|-----------------|  
|**Nome**|O nome da função.|  
|**% de Tempo Inclusivo Decorrido**|O percentual de todo o tempo nos dados de criação de perfil gasto pela função na execução do código em seu corpo e nas funções chamadas por ela.|  
|**% de Tempo Exclusivo Decorrido**|O percentual de todo o tempo nos dados de criação de perfil que a função gastou na execução do código no corpo da função. O tempo gasto em funções que foram chamadas pela função não é incluído.|  
  
## <a name="functions-with-most-individual-work"></a>Funções com mais trabalho individual  
 Uma lista das funções que consumiram mais tempo executando o código no corpo da função e não em funções que foram chamadas por ela.  
  
 **Funções com a maior parte do trabalho individual** inclui os seguintes dados para cada função:  
  
|Column|DESCRIÇÃO|  
|------------|-----------------|  
|**Nome**|O nome da função.|  
|**% de tempo exclusivo**|O percentual de todo o tempo nos dados de criação de perfil que a função gastou na execução do código no corpo da função. O tempo gasto em funções que foram chamadas pela função não é incluído.|  
  
## <a name="see-also"></a>Veja também  
 [Exibição Resumo](../profiling/summary-view-sampling-data.md)   
 [Exibição de Resumo](../profiling/summary-view-dotnet-memory-data.md)
