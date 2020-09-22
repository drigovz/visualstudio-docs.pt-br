---
title: Coletando Dados de Memória por meio de um Aplicativo Web ASP .NET Usando a Linha de Comando do Criador de Perfil | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- profiling tools,.NET memory method
ms.assetid: 57acf2b0-327a-4c0e-8078-ac2f6d99457d
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f7c759d4c2c4760be6782a518f4cdf209e828d4
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2020
ms.locfileid: "90839255"
---
# <a name="collecting-memory-data-from-an-aspnet-web-application-by-using-the-profiler-command-line"></a>Coletando dados de memória a partir de um aplicativo Web do ASP.NET usando a linha de comando do criador de perfil
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta seção descreve os procedimentos e as opções para coletar alocação de memória e dados de tempo de vida do objeto para um aplicativo Web ASP .NET usando a ferramenta de linha de comando **VSPerfCmd**.  
  
> [!NOTE]
> A ferramenta **VSPerfCmd** dá acesso completo à funcionalidade de Ferramentas de Criação de Perfil, inclusive pausar e retomar a criação de perfil e coletar dados adicionais do processador e de contadores de desempenho do Windows. Também é possível usar a ferramenta de linha de comando **VSPerfASPNETCmd** quando essa funcionalidade não for necessária. Em comparação com a ferramenta de linha de comando [VSPerfCmd](../profiling/vsperfcmd.md), nenhuma variável de ambiente precisa ser definida nem é necessário reiniciar o computador. Para obter mais informações, consulte [Rapid Web site profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  
  
## <a name="common-tasks"></a>Tarefas comuns  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Anexar o criador de perfil a um aplicativo ASP.NET em execução**|-   [Como Anexar o Criador de Perfil a um Aplicativo Web ASP .NET para Coletar Dados de Memória](../profiling/how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line.md)|  
|**Instrumentar binários compilados estatisticamente**|-   [Como Instrumentar um Aplicativo do ASP.NET Compilado Estaticamente e Coletar Dados de Memória](../profiling/how-to-instrument-a-statically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
|**Instrumentar binários compilados dinamicamente**|-   [Como instrumentar um aplicativo ASP.NET compilado dinamicamente e coletar dados de memória](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)|  
  
## <a name="related-tasks"></a>Related Tasks  
  
### <a name="profiling-aspnet-web-applications"></a>Criando perfil de aplicativos Web do ASP.NET  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar perfil usando o método de amostragem**|-   [Coletando estatísticas de aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-web-applications-using-the-profiler-sampling-method-from-the-command-line.md)|  
|**Criar perfil usando o método de instrumentação**|-   [Coletando dados de tempo detalhados usando a instrumentação](/visualstudio/profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method?view=vs-2015)|  
|**Criar perfil de contenção de recursos e atividade de thread**|-   [Coletando dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application-using-the-profiler-command-line.md)|  
  
### <a name="profiling-net-framework-memory-data"></a>Criando perfis de dados de memória do .NET Framework  
  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Coletando dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications-by-using-the-profiler-command-line.md)|  
|**Profile services (Serviços de perfil)**|-   [Coletando dados de memória do .NET](../profiling/collecting-memory-data-from-dotnet-framework-services-by-using-the-profiler-command-line.md)|  
  
### <a name="analyzing-net-memory-data-views-and-reports"></a>Analisando modos de exibição e relatórios de dados de memória do .NET  
 [Exibições de dados de memória do .NET](../profiling/dotnet-memory-data-views.md)  
  
## <a name="reference"></a>Referência  
 [Referência de Ferramentas de Criação de Perfil de linha de comando](../profiling/command-line-profiling-tools-reference.md)
