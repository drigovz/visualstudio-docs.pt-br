---
title: Introdução às ferramentas de desempenho | Microsoft Docs
description: Saiba mais sobre as diferentes maneiras que o Visual Studio oferece para coletar, exibir e analisar dados de desempenho de código.
ms.custom: SEO-VS-2020
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4f168c4c88ba12ff1f1c9bd0543e9d2b74ae095c
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801506"
---
# <a name="getting-started-with-performance-tools"></a>Introdução às ferramentas de desempenho

O Visual Studio oferece várias maneiras de coletar, exibir e analisar dados de desempenho do código. Em muitos casos, a melhor maneira de começar a usar as ferramentas de desempenho é usar as configurações padrão do **Assistente de desempenho**. O assistente coleta estatísticas de aplicativo que podem indicar problemas de desempenho em seu código.

- Avisos de desempenho que notificam você sobre problemas de codificação comuns são exibidos na janela **Lista de Erros** do Visual Studio. É possível navegar dos avisos para o código-fonte e para tópicos da ajuda detalhados que ajudarão a escrever um código mais eficiente.

- Os relatórios de desempenho fornecem exibições em diferentes níveis da estrutura, linhas de código-fonte e processos do seu aplicativo. Relatórios de desempenho mostram dados de execução do aplicativo, da chamada e funções chamadas de uma função específica à árvore de chamadas de todo o aplicativo.

Para criar um perfil rápido de um projeto, aplicativo ou site do ASP.net, selecione **depurar**  >  **criador de perfil de desempenho** e selecione **Assistente de desempenho**. Para obter instruções detalhadas, confira [Guia do iniciante à criação de perfil do desempenho](../profiling/beginners-guide-to-cpu-sampling.md) e [Como: coletar dados de desempenho de um Site da Web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Para especificar e configurar manualmente uma sessão de criação de perfil de desempenho, selecione **debug**  >  **Profiler**  >  **Gerenciador de desempenho**. Use a pasta **Destinos** e as páginas **Propriedades** no **Gerenciador de Desempenho** para configurar sessões. Para obter instruções, confira [How to: Manually create performance sessions](../profiling/how-to-manually-create-performance-sessions.md) (Como criar sessões de desempenho manualmente).

**Consulte também:**

- [Visão geral de ferramentas de desempenho](../profiling/overviews-performance-tools.md)
- [Analisando dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)
- [Usando regras de desempenho para analisar dados](../profiling/using-performance-rules-to-analyze-data.md)
- [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)
