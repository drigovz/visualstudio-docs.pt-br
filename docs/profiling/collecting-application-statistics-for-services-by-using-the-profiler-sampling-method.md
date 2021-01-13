---
title: Coletar estatísticas para serviços do Windows – método de amostragem do criador de perfil
description: Examine os procedimentos e as opções para coletar estatísticas de desempenho para serviços do Windows usando o método de amostragem de criação de perfil da linha de comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 07840ab2-3a92-4744-ac87-48b19e0ceecd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f4c686de4128d655b5b8146925529e6a280bb754
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148332"
---
# <a name="collect-application-statistics-for-services-by-using-the-profiler-sampling-method"></a>Coletar estatísticas do aplicativo para serviços usando o método de amostragem do criador de perfil
Esta seção descreve os procedimentos e as opções para coletar estatísticas de desempenho de serviços Windows usando o método de amostragem da linha de comando.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Anexar o criador de perfil a um serviço .NET**|-   [Como: anexar o criador de perfil a um serviço .NET para coletar estatísticas de aplicativo](../profiling/how-to-attach-the-profiler-to-a-dotnet-service-to-collect-application-statistics-by-using-the-command-line.md)|
|**Adicionar dados de interação de camada**|-   [Coletar dados de interação de camada](../profiling/adding-tier-interaction-data-from-the-command-line.md)|
|**Attach the profiler to a C/C++ service (Anexar o criador de perfil a um serviço C/C++)**|-   [Como: anexar o criador de perfil a um serviço nativo para coletar estatísticas de aplicativo](../profiling/how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line.md)|

## <a name="related-tasks"></a>Tarefas relacionadas

### <a name="profile-windows-services"></a>Criar perfil de serviços do Windows

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar perfil usando o método de instrumentação**|-   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-services-by-using-the-instrumentation-method.md)|
|**Profile .NET memory allocation and garbage collection (Criar o perfil de alocação de memória e coleta de lixo do .NET)**|-   [Coletar dados de memória do .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|
|**Criar perfil de contenção de recursos e atividade de thread**|-   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-a-service-by-using-the-profiler-command-line.md)|

### <a name="profile-by-using-the-sampling-method"></a>Criar perfil usando o método de amostragem

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-stand-alone-applications.md)|
|**Perfis de aplicativos Web ASP.NET**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|

### <a name="analyze-sampling-data-views-and-reports"></a>Analisar exibições e relatórios dos dados de amostragem
- [Exibições de dados do método de amostragem](../profiling/profiler-sampling-method-data-views.md)
