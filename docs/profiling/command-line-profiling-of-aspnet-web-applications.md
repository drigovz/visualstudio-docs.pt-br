---
title: Criação de perfil de linha de comando dos aplicativos Web ASP.NET | Microsoft Docs
description: Saiba como usar o Ferramentas de Criação de Perfil da linha de comando para coletar dados de desempenho para aplicativos Web ASP.NET.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profiling ASP.NET applications
- profling tools,ASP.NET applications
ms.assetid: 897c00d5-5767-433b-a960-4a29c6023ede
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: e97e6a3d9115be2b14cac4e87698c6eeb9fc091d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945182"
---
# <a name="command-line-profiling-of-aspnet-web-applications"></a>Criação de perfil de linha de comando dos aplicativos Web ASP.NET
Esta seção descreve os procedimentos e as opções para coletar dados de desempenho para [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativos Web usando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ferramentas de criação de perfil da linha de comando.

> [!NOTE]
> Os recursos de segurança aprimorados no Windows 8 e no Windows Server 2012 exigiram alterações significativas na maneira como o criador de perfil do Visual Studio coleta dados nessas plataformas. Os aplicativos UWP também requerem novas técnicas de coleta. Consulte [ferramentas de desempenho em aplicativos do Windows 8 e do Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="common-tasks"></a>Tarefas comuns

| Tarefa | Conteúdo relacionado |
| - | - |
| **Coletar dados básicos de criação de perfil ASP.NET facilmente:** use a ferramenta **VSPerfASPNETCmd** para coletar dados de amostragem, de instrumentação, de memória do .NET, de contenção ou de interação de camadas sem os requisitos de configuração e reinicializações do IIS (Serviços de Informações da Internet) necessárias para **VSPerfCmd**. **VSPerfASPNETCmd** não permite coletar dados adicionais ou para controlar a coleta de dados. **Observação:**  **VSPerfASPNETCmd** é a ferramenta preferida a ser usada para usar o criador de perfil autônomo para criar perfis de sites ASP.net. | -   [Criação rápida de perfil de site com VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) |
| **Coletar estatísticas do aplicativo:** use o método de amostragem para coletar estatísticas de desempenho. Os dados de amostragem são úteis para analisar problemas de uso da CPU e para entender as características de desempenho geral de um aplicativo. | -   [Coletar estatísticas do aplicativo usando amostragem](../profiling/collecting-application-statistics-for-aspnet-using-the-profiler-sampling-method.md) |
| **Coletar dados de tempo detalhados:** use o método de instrumentação para coletar informações de tempo detalhadas. Os dados de instrumentação são úteis para analisar problemas de E/S e para análise refinada de cenários de aplicativo. | -   [Coletar dados de tempo detalhados usando a instrumentação](../profiling/collecting-detailed-timing-data-aspnet-profiler-instrumentation-method.md) |
| **Coletar dados de memória do .NET:** use a amostragem ou a instrumentação para coletar dados de alocação de memória do .NET que mostra o tamanho e o número de objetos alocados. Também é possível coletar dados de tempo de vida do objeto que mostram o tamanho e o número de objetos recuperados em cada geração de coleta de lixo. | -   [Coletar dados de memória](../profiling/collecting-memory-data-from-an-aspnet-web-application.md) |
| **Coletar dados de simultaneidade:** use o método de simultaneidade para coletar dados de contenção de recursos. **Observação:**  Não há suporte para a coleta de dados de visualização e atividade de thread para aplicativos Web. | -   [Coletar dados de simultaneidade](../profiling/collecting-concurrency-data-for-an-aspnet-web-application.md) |
| **Adicionar dados de interação de camada:** Você pode adicionar dados de desempenho sobre [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] chamadas síncronas que o [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplicativo Web faz para um banco de dados da Microsoft [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] . | -   [Coletar dados de interação de camada](../profiling/adding-tier-interaction-data-from-the-command-line.md) |

## <a name="related-tasks"></a>Tarefas relacionadas

|Tarefa|Conteúdo relacionado|
|----------|---------------------|
|**Criar o perfil de aplicativos autônomos (clientes)**|-   [Perfis de aplicativos autônomos](../profiling/command-line-profiling-of-stand-alone-applications.md)|
|**Profile services (Serviços de perfil)**|-   [Profile services (Serviços de perfil)](../profiling/command-line-profiling-of-services.md)|
