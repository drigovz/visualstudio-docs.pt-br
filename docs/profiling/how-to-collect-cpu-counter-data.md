---
title: 'Como: Coletar dados do contador de CPU | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.cpucounters
helpviewer_keywords:
- profiling tools, using portable CPU counters
- performance tools, portable CPU counters
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c607263c6b6f6472258aaeab1c3187efaf30a120
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62973975"
---
# <a name="how-to-collect-cpu-counter-data"></a>Como: Coletar dados do contador de CPU

Um contador de evento de CPU é usado para coletar dados de desempenho específicos de hardware. Este artigo mostra como coletar dados do contador de eventos quando você usa o método de criação de perfil de instrumentação.

Dois tipos de eventos do contador de CPU ocorrem:

- Eventos portáteis – eventos de CPU que podem ser coletados, independentemente da CPU específica.

- Eventos de plataforma – eventos de CPU que estão acoplados a uma CPU específica.

  Os eventos portáteis incluem eventos gerais, como Instruções Desativadas e Ciclos Não Interrompidos, eventos de buffer de CPU, eventos de ramificação e eventos de cache L2. Os contadores de evento de plataforma disponíveis são determinados pelo fabricante do processador.

  Categorias de eventos podem ser compartilhadas entre contadores de plataforma e portáteis. Por exemplo, as seguintes categorias de dados são frequentemente comuns aos dois tipos:

- Eventos de memória.

- Eventos de front-end.

- Eventos de ramificação.

  Colete dados do contador de desempenho de duas formas no criador de perfil:

- Colete dados de um ou mais contadores ao analisar por instrumentação.

- Especifique um evento de contador como o intervalo de amostragem, quando você analisar por amostragem. Para obter mais informações, confira [Como: Escolher eventos de amostragem](../profiling/how-to-choose-sampling-events.md).

## <a name="to-collect-cpu-performance-counter-data-when-you-profile-by-instrumentation"></a>Para coletar dados de contador de desempenho de CPU ao analisar por instrumentação

1. Nas **Páginas de Propriedade** da sessão de desempenho, clique em **Contadores de CPU.**

2. Selecione a caixa de seleção **Coletar Contadores de CPU**.

3. Expanda a árvore **Contadores de desempenho disponíveis** até localizar os eventos de amostragem que você deseja coletar.

4. Para cada evento que você deseja coletar, selecione o evento e, em seguida, clique na seta à direita para adicionar o evento à lista de **Contadores Selecionados**.

    > [!NOTE]
    > **Contadores de desempenho disponíveis** estará habilitada somente se você selecionar a caixa de seleção **Coletar Contadores de CPU**.

## <a name="see-also"></a>Consulte também

[Configurar sessões de desempenho](../profiling/configuring-performance-sessions.md)
[Propriedades da sessão de desempenho](../profiling/performance-session-properties.md)
[Contadores da CPU e do Windows](../profiling/cpu-and-windows-counters.md)
[Como: Escolher eventos de amostragem](../profiling/how-to-choose-sampling-events.md)