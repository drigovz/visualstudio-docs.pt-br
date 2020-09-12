---
title: Visualização Simultânea | Microsoft Docs
ms.date: 07/11/2017
ms.topic: conceptual
f1_keywords:
- vs.cv.performance.viewnavigation
- vs.cv.overview
- vs.cv.performance.gettingstarted
- vs.cv.gettingstarted
helpviewer_keywords:
- Concurrency Visualizer, Concurrency Visualizer
ms.assetid: ae5879a0-1e1a-455a-ba72-148e57f59289
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a955304e1a0939bbe7398b48a5e9ff30461d8745
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037335"
---
# <a name="concurrency-visualizer"></a>Visualizador de Simultaneidade

> [!NOTE]
> A Visualização Simultânea é uma extensão opcional do Visual Studio. Baixe a Visualização Simultânea e a Coleção de Ferramentas de Visualização Simultânea nos seguintes links:
>
> - Baixe o [Visualizador de simultaneidade para a extensão do Visual Studio 2019](https://marketplace.visualstudio.com/items?itemName=Diagnostics.DiagnosticsConcurrencyVisualizer2019#overview) .
> - Baixe a extensão [Visualização Simultânea para Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ConcurrencyVisualizer2017#overview).
> - Baixe o [Visualizador de simultaneidade para a extensão do Visual Studio 2015](https://marketplace.visualstudio.com/items?itemName=Diagnostics.ConcurrencyVisualizerforVisualStudio2015) .
> - Baixe a [Coleção de Ferramentas da Visualização Simultânea para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=49103).
>
> O [CVCollectionCmd (Utilitário de Linha de Comando Visualização Simultânea)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md) permite coletar rastreamentos na linha de comando que podem ser exibidos na Visualização Simultânea para Visual Studio 2015. A ferramenta pode ser usada em computadores que não tenham o Visual Studio instalado.

É possível usar a Visualização Simultânea para ver como é o desempenho do seu aplicativo multithread. As exibições na Visualização Simultânea oferecem dados gráficos, tabulares e textuais que mostram as relações temporais entre os threads no programa e o sistema como um todo. É possível usar a Visualização Simultânea para localizar gargalos de desempenho, subutilização da CPU, contenção de thread, migração de thread entre núcleos, atrasos de sincronização, atividade do DirectX, áreas de E/S sobrepostas e outras informações. As exibições fornecem dados em que você pode agir vinculando sua saída gráfica a pilhas de chamadas e código-fonte.

> [!NOTE]
> A Visualização Simultânea não oferece suporte a projetos Web.

A Visualização Simultânea conta com a funcionalidade [Rastreamento de Eventos para Windows](/windows/win32/etw/event-tracing-portal).

## <a name="related-topics"></a>Tópicos relacionados

|Title|Descrição|
|-----------|-----------------|
|[Exibição da utilização](../profiling/utilization-view.md)|Descreve como exibir e analisar a atividade do sistema entre todos os processadores.|
|[Modo de Exibição de Threads](../profiling/threads-view-parallel-performance.md)|Descreve como analisar as interações entre threads no programa.|
|[Exibição de núcleos](../profiling/cores-view.md)|Descreve como analisar a migração de thread entre núcleos.|
|[Padrões comuns para aplicativos multi-threaded com mau comportamento](../profiling/common-patterns-for-poorly-behaved-multithreaded-applications.md)|Descreve diversos padrões em comum e mostra como eles são exibidos na Visualização Simultânea.|
|[Desenvolvimento paralelo no blog do Visual Studio](/archive/blogs/visualizeparallel/)|Dá dicas e práticas recomendadas para a Visualização Simultânea.|
|[Exibições do relatório de desempenho](../profiling/performance-report-views.md)|Fornece informações de referência sobre os relatórios e as exibições das Ferramentas de Criação de Perfil do Visual Studio.|
|[SDK do Visualizador de Simultaneidade](../profiling/concurrency-visualizer-sdk.md)|Descreve como instrumentalizar o código-fonte para exibir informações adicionais na Visualização Simultânea.|
|[Utilitário de linha de comando do Visualizador de simultaneidade (CVCollectionCmd)](../profiling/concurrency-visualizer-command-line-utility-cvcollectioncmd.md)|Descreve como usar o utilitário de linha de comando Visualização Simultânea (CVCollectionCmd.exe) para coletar e processar rastreamentos em máquinas que não tenham o Visual Studio.|

## <a name="see-also"></a>Confira também

- [Criação de perfis no Visual Studio](../profiling/index.yml)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)