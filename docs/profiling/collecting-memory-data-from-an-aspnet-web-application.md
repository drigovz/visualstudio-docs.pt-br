---
title: Obter dados de memória do aplicativo Web ASP.NET usando a linha de comando do criador de perfil
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 9e8d9fde00a2390793ae8efe05b684e73caca321
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74773053"
---
# <a name="collect-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Coletar dados de memória por meio de um aplicativo Web ASP.NET usando a linha de comando do criador de perfil
Esta seção descreve os procedimentos e as opções para coletar alocação de memória e dados de tempo de vida do objeto para um aplicativo Web ASP .NET usando a ferramenta de linha de comando **VSPerfCmd**.

> [!NOTE]
> A ferramenta **VSPerfCmd** dá acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar a criação de perfil e coletar dados adicionais do processador e de contadores de desempenho do Windows. Também é possível usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando essa funcionalidade não for necessária. Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), nenhuma variável de ambiente precisa ser definida nem é necessário reiniciar o computador. Para saber mais, confira [Criação de perfil de site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).

## <a name="common-tasks"></a>Tarefas comuns

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Anexar o criador de perfil a um aplicativo ASP.NET em execução**|-   [Como: Anexar o profiler a um aplicativo web ASP.NET para coletar dados de memória](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|
|**Instrumentar binários compilados estatisticamente**|-   [Como: Instrumentar um aplicativo de ASP.NET compilado estáticamente e coletar dados de memória](../profiling/how-to-instrument-a-statically-compiled-aspnet-app-and-collect-memory-data.md)|
|**Instrumentar binários compilados dinamicamente**|-   [Como: Instrumentar um aplicativo de ASP.NET compilado dinamicamente e coletar dados de memória](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)|

## <a name="related-tasks"></a>Tarefas relacionadas

### <a name="profile-aspnet-web-applications"></a>Criar o perfil de aplicativos Web ASP.NET

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar perfil usando o método de amostragem**|-   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md)|
|**Criar perfil usando o método de instrumentação**|-   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md)|
|**Criar perfil de contenção de recursos e atividade de thread**|-   [Coletar dados de concorrência](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md)|

### <a name="profile-net-framework-memory-data"></a>Criar perfis de dados de memória do .NET Framework

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Coletar dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md)|
|**Profile services (Serviços de perfil)**|-   [Coletar dados de memória .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|

### <a name="analyze-net-memory-data-views-and-reports"></a>Analisar modos de exibição e relatórios de dados de memória do .NET
- [Exibições de dados de memória .NET](../profiling/dotnet-memory-data-views.md)

## <a name="reference"></a>Referência
- [Referência de ferramentas de criação de perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)
