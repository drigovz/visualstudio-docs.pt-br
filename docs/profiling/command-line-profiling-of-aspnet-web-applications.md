---
title: Criação de perfil de linha de comando dos aplicativos Web ASP.NET | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 2b2f4602e56a89452635ebe0ad94dbc1664c2fb3
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "53835338"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Criação de perfil de linha de comando dos aplicativos Web ASP.NET
Esta seção descreve os procedimentos e as opções para coletar dados de desempenho para aplicativos Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] usando as Ferramentas de Criação de Perfil do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] na linha de comando.  
  
> [!NOTE]
>  Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [Ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="common-tasks"></a>Tarefas comuns
  
| Tarefa | Conteúdo relacionado |
| - | - |
| **Coletar dados de criação de perfil básica do ASP.NET com facilidade:** Use a ferramenta **VSPerfASPNETCmd** para coletar dados de amostragem, de instrumentação, de memória do .NET, de contenção ou de interação de camadas sem os requisitos de configuração e reinicializações do IIS (Serviços de Informações da Internet) necessárias para **VSPerfCmd**. **VSPerfASPNETCmd** não permite coletar dados adicionais ou para controlar a coleta de dados. **Observação:**  A **VSPerfASPNETCmd** é a ferramenta de preferência para usar o criador de perfil autônomo para criar o perfil de sites Web ASP.NET. | -   [Criação de perfil de site rápida com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Coletar estatísticas do aplicativo:** Use o método de amostragem para coletar estatísticas de desempenho. Os dados de amostragem são úteis para analisar problemas de uso da CPU e para entender as características de desempenho geral de um aplicativo. | -   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Coletar dados detalhados:** Usar o método de instrumentação para coletar informações de tempo detalhadas. Os dados de instrumentação são úteis para analisar problemas de E/S e para análise refinada de cenários de aplicativo. | -   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Coletar dados de memória do .NET:** Use a amostragem ou a instrumentação para coletar dados de alocação de memória do .NET que mostra o tamanho e o número de objetos alocados. Também é possível coletar dados de tempo de vida do objeto que mostram o tamanho e o número de objetos recuperados em cada geração de coleta de lixo. | -   [Coletar dados de memória](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Coletar dados de simultaneidade:** Use o método de simultaneidade para coletar dados de contenção de recursos. **Observação:**  A coleta de atividade do thread e de dados de visualização para aplicativos Web não é uma ação compatível. | -   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Adicionar dados de interação entre camadas:** É possível adicionar dados de desempenho sobre chamadas [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] síncronas que o aplicativo Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] efetua para um banco de dados [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] da Microsoft. | -   [Coletar dados de interação entre camadas](../profiling/adding-tier-interaction-data-from-the-command-line.md) |
  
## <a name="related-tasks"></a>Tarefas relacionadas

  
|Tarefa|Conteúdo relacionado|  
|----------|---------------------|  
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Criar perfil de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)|  
|**Profile services (Serviços de perfil)**|-   [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)|