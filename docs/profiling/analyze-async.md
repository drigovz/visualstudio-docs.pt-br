---
title: Analisar o desempenho do código assíncrono do .NET | Microsoft Docs
description: Use a ferramenta Async do .NET para analisar o desempenho do código assíncrono. Há tempo para cada tarefa listada. Para ver o código, use ir para arquivo de origem.
ms.custom: SEO-VS-2020
ms.date: 5/5/2020
ms.topic: conceptual
helpviewer_keywords:
- asynchronous, async, profiling
author: esteban-herrera
ms.author: esherrer
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 86575cd71c41ac8ac874e9b62f8273ee46e02c57
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205483"
---
# <a name="analyze-performance-of-net-asynchronous-code"></a>Analisar o desempenho do código assíncrono do .NET

Use a ferramenta Async do .NET para analisar o desempenho do código assíncrono em seu aplicativo.

> [!NOTE]
> A ferramenta Async do .NET requer o Visual Studio 2019 versão 16,7 ou posterior e um projeto .NET que usa **Async** e **Await**.

## <a name="setup"></a>Instalação

1. Selecione **ALT + F2** para abrir o criador de perfil de desempenho no Visual Studio.

1. Marque a caixa de seleção **.net Async** .

   ![Ferramenta assíncrona do .NET selecionada](../profiling/media/async-tool-selected.png "Ferramenta assíncrona do .NET selecionada")

1. Clique no botão **Iniciar** para executar a ferramenta.

1. Depois que a ferramenta começar a ser executada, percorra o cenário no qual você deseja criar o perfil em seu aplicativo. Em seguida, selecione **parar coleta** ou feche seu aplicativo para ver seus dados.

1. Após a coleta parar, você verá uma tabela das atividades que ocorreram durante a sessão de criação de perfil.

   ![Ferramenta Async do .NET interrompida](../profiling/media/async-tool-opened.png "Ferramenta Async do .NET interrompida")

Os eventos assíncronos são organizados em atividades cronologicamente. Cada exibe a hora de início, a hora de término e a duração.

Cada linha que corresponde a uma [tarefa](/dotnet/api/system.threading.tasks) é rotulada na coluna **nome** . Para qualquer nome de tarefa que não pode ser resolvido, uma **tarefa no** rótulo é exibida. Ele é seguido pelo nome do método no qual a tarefa ocorre. Se uma atividade assíncrona não for concluída na sessão de coleta, um rótulo **incompleto** aparecerá na coluna **hora de término** .

Para investigar melhor uma tarefa ou atividade específica, clique com o botão direito do mouse na linha. Em seguida, selecione **ir para o arquivo de origem** para ver onde o código ocorreu na atividade.

![Ferramenta Async do .NET com ir para arquivo de origem selecionado](../profiling/media/async-tool-gotosource.png "Ferramenta Async do .NET com ir para arquivo de origem selecionado")

## <a name="see-also"></a>Confira também

- [Otimizando as configurações do criador de perfil](../profiling/optimize-profiler-settings.md)