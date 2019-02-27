---
title: Criação de perfil de linha de comando de aplicativos autônomos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profillng tools,stand-alone applications
- profling stand-alone applications
ms.assetid: a47f2bf2-186d-4120-bb79-34e2f3a1ee42
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcd48f421dcae74e82b0d9249a958f2a834f0a45
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56603281"
---
# <a name="command-line-profiling-of-stand-alone-applications"></a>Criação de perfil de linha de comando para aplicativos autônomos
Esta seção descreve os procedimentos e as opções para coletar dados de desempenho para aplicativos autônomos (clientes) usando as Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na linha de comando.

## <a name="common-tasks"></a>Tarefas comuns

| Tarefa | Conteúdo relacionado |
| - | - |
| **Coletar estatísticas do aplicativo:** Use o método de amostragem para coletar estatísticas de desempenho. Os dados de amostragem são úteis para analisar problemas de utilização de CPU e para entender as características de desempenho geral de um aplicativo. | -   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-stand-alone-applications.md) |
| **Coletar dados detalhados:** Usar o método de instrumentação para coletar informações de tempo detalhadas. Os dados de instrumentação são úteis para analisar problemas de E/S e para análise refinada de cenários de aplicativo. | -   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-for-a-stand-alone-application.md) |
| **Coletar dados de memória do .NET:** Use a amostragem ou a instrumentação para coletar dados de alocação de memória do .NET que mostra o tamanho e o número de objetos alocados. Também é possível coletar dados de tempo de vida do objeto que mostram o tamanho e o número de objetos recuperados em cada geração de coleta de lixo. | -   [Coletar dados de memória do .NET Framework](../profiling/collecting-dotnet-framework-memory-data-for-stand-alone-applications.md) |
| **Coletar dados de simultaneidade:** Use o método de simultaneidade para coletar dados de contenção de recursos e dados de atividade do thread que mostram a utilização da CPU, contenção e migração de threads, atrasos na sincronização, áreas de E/S sobrepostas e outros eventos do sistema. | -   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-stand-alone-applications.md) |
| **Adicionar dados de interação de camada:** É possível adicionar dados de desempenho sobre chamadas ADO.NET síncronas que o aplicativo efetuou para um banco de dados [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] da Microsoft. Adicionar dados de interação de camada a uma execução de criação de perfil requer procedimentos específicos com ferramentas de criação de perfil de linha de comando. | -   [Coletar dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
| **Experimente:** Use procedimentos passo a passo para criar o perfil de um aplicativo cliente de exemplo usando o método de amostragem ou de instrumentação. | -   [Passo a passo: Criação de perfil de linha de comando usando amostragem](../profiling/walkthrough-command-line-profiling-using-sampling.md)<br />-   [Passo a passo: Criação de perfil de linha de comando usando instrumentação](/visualstudio/profiling/command-line-profiling-of-stand-alone-applications) |

## <a name="related-tasks"></a>Tarefas relacionadas

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Aplicativos ASP.NET do perfil**|-   [Criar o perfil de aplicativos Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)|
|**Profile services (Serviços de perfil)**|-   [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)|