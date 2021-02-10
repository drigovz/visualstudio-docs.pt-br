---
title: Exibições de dados de memória do .NET | Microsoft Docs
description: Consulte links para informações de referência para os modos de exibição e relatórios de arquivos de dados do profiler que contêm dados de criação de perfil de memória do .NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method views
- profiling tools,.NET memory profiling views
ms.assetid: 79184d8e-769b-4ace-be2b-521147772081
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1a60b51571d33a619cdc04c534f6b77fafcb584f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955275"
---
# <a name="net-memory-data-views"></a>Exibições de dados da memória do .NET
Esta seção contém informações de referência para as exibições e os relatórios dos arquivos de dados do criador de perfil que contêm os dados de criação de perfil de memória do .NET.

## <a name="in-this-section"></a>Nesta seção
- [Exibição do Resumo](../profiling/summary-view-dotnet-memory-data.md)

 Lista as funções e os tipos que alocaram mais memória.

- [Exibição de alocações](../profiling/dotnet-memory-allocations-view.md)

 Lista os tipos que foram alocados na execução de criação de perfil e as árvores de chamada (caminhos de execução) que resultaram na alocação do tipo.

- [Exibição do tempo de vida do objeto](../profiling/object-lifetime-view.md)

 Lista os tipos que foram alocados na execução de criação de perfil e o número de instâncias, tamanho em bytes e a geração de coleta de lixo do tipo.

- [Exibição de árvore de chamadas-amostragem](../profiling/call-tree-view-dotnet-memory-sampling-data.md)

 Exibe uma árvore hierárquica que representa os caminhos de execução e os dados de alocação de memória das funções de execução de criação de perfil.

- [Exibição de módulos – Amostragem](../profiling/modules-view-dotnet-memory-sampling-data.md)

 Organiza os dados de alocação de memória .NET por módulo e lista as funções, as linhas de código-fonte e as instruções que estavam em execução quando a memória foi alocada.

- [Exibição Caller/Callee-dados de amostragem de memória .NET](../profiling/caller-callee-view-dotnet-memory-sampling-data.md)

 Lista os dados de alocação de memória para uma função selecionada, as funções que chamaram a função selecionada e as funções que foram chamadas pela função selecionada.

- [Exibição de funções – Amostragem](../profiling/functions-view-dotnet-memory-sampling-data.md)

 Lista os dados de alocação de memória para as funções na execução de criação de perfil.

- [Exibição de Linhas – Amostragem](../profiling/lines-view-dotnet-memory-sampling-data.md)

 Lista os dados de alocação de memória para as linhas de código-fonte das funções na execução de criação de perfil.

- [Exibição de ponteiros de instrução (IPs) – Amostragem](../profiling/instruction-pointers-ips-view-dotnet-memory-sampling-data.md)

 Lista os dados de alocação de memória para as instruções de funções na execução de criação de perfil.

- [Exibição de árvore de chamadas-instrumentação](../profiling/call-tree-view-dotnet-memory-instrumentation-data.md)

 Exibe uma árvore hierárquica que representa os caminhos de execução, os dados de alocação de memória e os dados de tempo detalhados das funções instrumentadas da execução de criação de perfil.

- [Exibição de módulos-instrumentação](../profiling/modules-view-dotnet-memory-instrumentation-data.md)

 Organiza os dados de criação de perfil por módulo e lista as funções, os dados de alocação de memória e as informações detalhadas de tempo para o módulo.

- [Exibição do chamador/receptor-dados de instrumentação de memória de rede](../profiling/caller-callee-view-net-memory-instrumentation-data.md)

 Lista os dados de alocação de memória e informações de tempo detalhadas para uma função instrumentada selecionada, as funções que chamaram a função selecionada e as funções que foram chamadas pela função selecionada.

- [Exibição de funções – Instrumentação](../profiling/functions-view-dotnet-memory-instrumentation-data.md)

 Lista os dados de alocação de memória para as funções instrumentadas na execução de criação de perfil.

## <a name="reference"></a>Referência
- [Exibição de detalhes da função](../profiling/function-details-view.md)

 Exibe um gráfico da relação entre uma função selecionada e as funções que chamaram e foram chamadas pela função selecionada.

- [Exibição de processo](../profiling/process-view.md)

 Lista o processo e as horas final e inicial do thread.

- [Exibição de marcas](../profiling/marks-view.md)

 Lista ETW e eventos de amostragem inseridos em um arquivo de dados de criação de perfil.

## <a name="related-sections"></a>Seções relacionadas
- [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)

 Informações de referência sobre as exibições e os relatórios dos arquivos de dados do criador de perfil que foram gerados usando o método de amostragem.

- [Exibições de dados do método de instrumentação](../profiling/instrumentation-method-data-views.md)

 As informações de referência sobre as exibições e os relatórios dos arquivos de dados do criador de perfil que foram gerados usando o método de instrumentação.
