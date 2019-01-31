---
title: Exibição Resumo – Dados de amostragem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method, Summary view
- Summary view
ms.assetid: 79056873-2985-40be-9112-cdbc26a65156
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8570692ec620ee50cd24f3fa95ceec8b21172919
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803079"
---
# <a name="summary-view---sampling-data"></a>Exibição Resumo – Dados de amostragem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A exibição Resumo exibe informações sobre as funções mais caras de desempenho em uma execução da criação de perfil. Para obter mais informações, incluindo uma descrição das listas Links de notificação e Relatório, consulte [Exibição Resumo](../profiling/summary-view.md).  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos da Windows Store também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="timeline-graph"></a>Gráfico de linha do tempo  
 O gráfico de linha do tempo na exibição Resumo mostra o percentual da utilização do processador (CPU) do aplicativo com perfil ao longo do tempo em que ocorreu a criação de perfil. É possível usar o gráfico de linha do tempo para filtrar a exibição para um intervalo de tempo selecionado. Para obter mais informações, confira [Como: Filtrar as exibições de relatório da linha do tempo resumida](../profiling/how-to-filter-report-views-from-the-summary-timeline.md).  
  
## <a name="hot-path"></a>Afunilamento  
 O **Afunilamento** exibe o caminho de execução no qual a maioria das amostras foi coletada. É possível clicar em uma função para mostrar a exibição Detalhes da Função referente a ela. Para exibir outras exibições da função, clique com o botão direito do mouse na função e, em seguida, clique em uma exibição na lista.  
  
 O **Afunilamento** inclui os seguintes dados para cada função:  
  
|Column|Descrição|  
|------------|-----------------|  
|**Nome**|O nome da função.|  
|**% de Amostras Inclusivas**|O percentual de todas as amostras que ocorreram quando essa função ou uma função chamada por essa função estava em execução.|  
|**% de Amostras Exclusivas**|O percentual de todas as amostras que ocorreram durante a execução de código pela função em seu corpo. As amostras coletadas em funções chamadas por essa função não são incluídas.|  
  
## <a name="functions-doing-most-individual-work"></a>Funções Que Realizam a Maioria do Trabalho Individual  
 A lista **Funções que realizam a maior parte do trabalho individual** exibe as funções que têm o maior número de amostras exclusivas na execução de criação de perfil. Uma amostra exclusiva é atribuída a uma função se a função está executando seu próprio código quando a amostra foi coletada. Uma amostra exclusiva não é atribuída a uma função se a função está chamando outra função quando a amostra foi coletada. Um grande número de amostras exclusivas indica que um tempo significativo foi gasto na própria função.  
  
 É possível clicar em uma função para mostrar a exibição Detalhes da Função referente a ela. Para exibir outras exibições da função, clique com o botão direito do mouse na função e, em seguida, clique em uma exibição na lista.  
  
 **Funções que realizam a maior parte do trabalho individual** inclui os seguintes dados para cada função:  
  
|Column|Descrição|  
|------------|-----------------|  
|**Nome**|O nome da função.|  
|**% de Amostras Exclusivas**|O percentual de todas as amostras na execução de criação de perfil coletadas durante a execução de código pela função em seu corpo. O percentual exclui as amostras que foram coletadas quando as funções chamadas por essa função estavam em execução.|  
  
## <a name="see-also"></a>Consulte também  
 [Exibição Resumo](../profiling/summary-view-dotnet-memory-data.md)   
 [Exibição de Resumo](../profiling/summary-view-instrumentation-data.md)
