---
title: Coletando dados de simultaneidade para um serviço usando a linha de comando do criador de perfil | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 275aacba-b2af-4d34-8931-ee30d777a256
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5df8fa1b0e0d9c76595c29958641de628e5e8b78
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440214"
---
# <a name="collect-concurrency-data-for-a-service-by-using-the-profiler-command-line"></a>Coletar dados de simultaneidade para um serviço usando a linha de comando do criador de perfil
O método de simultaneidade das Ferramentas de Criação de Perfil [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] permite coletar dados de contenção de recursos e dados de atividade do thread que mostram a utilização da CPU, contenção e migração do thread, atrasos na sincronização, áreas de ES sobrepostas e outros eventos do sistema.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Attach to a running .NET service (Anexar a um serviço do .NET em execução)**|-   [Como: Anexar o criador de perfil a um serviço do .NET para coletar dados de simultaneidade](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-concurrency-data-by-using-the-command-line.md)|
|**Add tier-interaction data (Adicionar dados de interação de camada)**|-   [Coletar dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Anexar a um serviço do C/C++ em execução**|-   [Como: Anexar o criador de perfil a um serviço nativo para coletar dados de simultaneidade](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tarefas relacionadas

### <a name="profile-windows-services"></a>Criar perfil de serviços do Windows

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar perfil usando o método de amostragem**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-services-by-using-the-profiler-sampling-method.md)|
|**Criar perfil usando o método de instrumentação**|-   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Criar o perfil de alocação de memória e coleta de lixo do .NET**|-   [Coletar dados de memória do .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="profile-concurrency-data"></a>Criar perfil de dados de simultaneidade

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Aplicativos Autônomos de Perfil**|-   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-stand-alone-applications.md)|
|**Criar o perfil de aplicativos Web ASP.NET**|-   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="analyze-concurrency-data-views-and-reports"></a>Analisar modos de exibição e relatórios de Dados de Simultaneidade
- [Exibições de dados da contenção de recurso](../profiling/resource-contention-data-views.md)

- [Visualização Simultânea](../profiling/concurrency-visualizer.md)

## <a name="reference"></a>Referência
- [Referência de ferramentas de criação de perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)