---
title: Introdução às ferramentas de desempenho | Microsoft Docs
ms.date: 11/04/2018
ms.topic: conceptual
helpviewer_keywords:
- getting started, performance
- getting started, profiling tools
ms.assetid: 02085214-a8e4-40fd-9b26-32391a7a7082
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2602996e6c823888b272129ea0c2414534a4e1f7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969661"
---
# <a name="getting-started-with-performance-tools"></a>Introdução às ferramentas de desempenho

O Visual Studio oferece várias maneiras de coletar, exibir e analisar dados de desempenho do código. Em muitos casos, a melhor maneira de começar a usar as ferramentas de desempenho é usar as configurações padrão do **Assistente de desempenho**. O assistente coleta estatísticas de aplicativo que podem indicar problemas de desempenho em seu código.

- Avisos de desempenho que notificam você sobre problemas de codificação comuns são exibidos na janela **Lista de Erros** do Visual Studio. É possível navegar dos avisos para o código-fonte e para tópicos da ajuda detalhados que ajudarão a escrever um código mais eficiente.

- Os relatórios de desempenho fornecem exibições em diferentes níveis da estrutura, linhas de código-fonte e processos do seu aplicativo. Relatórios de desempenho mostram dados de execução do aplicativo, da chamada e funções chamadas de uma função específica à árvore de chamadas de todo o aplicativo.

Para criar o perfil de um projeto, aplicativo ou site do ASP.NET rapidamente, selecione **Depurar** > **Criador de Perfil de Desempenho** e selecione **Assistente de Desempenho**. Para obter instruções detalhadas, veja [Guia do iniciante à criação de perfil do desempenho](../profiling/beginners-guide-to-cpu-sampling.md) e [Como: Coletar dados de desempenho para um site da Web](../profiling/how-to-collect-performance-data-for-a-web-site.md).

Para especificar e configurar uma sessão de criação de perfil de desempenho manualmente, selecione **Depurar** > **Criador de Perfil** > **Gerenciador de Desempenho**. Use a pasta **Destinos** e as páginas **Propriedades** no **Gerenciador de Desempenho** para configurar sessões. Para obter instruções, veja [Como: Criar sessões de desempenho manualmente](../profiling/how-to-manually-create-performance-sessions.md).

**Confira também:**

- [Visões gerais das ferramentas de desempenho](../profiling/overviews-performance-tools.md)
- [Analisando dados de ferramentas de desempenho](../profiling/analyzing-performance-tools-data.md)
- [Usando regras de desempenho para analisar dados](../profiling/using-performance-rules-to-analyze-data.md)
- [Configurando sessões de desempenho](../profiling/configuring-performance-sessions.md)