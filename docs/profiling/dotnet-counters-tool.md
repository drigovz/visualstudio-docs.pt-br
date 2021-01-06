---
title: Visualizar contadores dotnet | Microsoft Docs
description: Aprenda a usar a ferramenta de contadores do .NET no criador de perfil de desempenho do Visual Studio.
ms.date: 12/7/2020
ms.topic: conceptual
helpviewer_keywords:
- dotnet, counters, profiling
author: sagar-shetty
ms.author: sashe
manager: AndSter
ms.workload:
- multiple
ms.openlocfilehash: 7a09cc073b2886ab0d374bccaf8b85f3bb729dd7
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97905011"
---
# <a name="visualize-dotnet-counters-from-the-visual-studio-profiler"></a>Visualizar contadores dotnet do criador de perfil do Visual Studio


A ferramenta de contadores do .NET permite que você visualize [contadores dotnet](/dotnet/core/diagnostics/dotnet-counters) ao longo do tempo diretamente no criador de perfil do Visual Studio.


> [!NOTE]
> A ferramenta de contadores do .NET requer o Visual Studio 2019 versão 16,7 ou posterior e tem como alvo o .NET Core 3.0 +.

## <a name="setup"></a>Instalação

1. Abra o criador de perfil de desempenho (**ALT + F2** ou **debug-> Profiler de desempenho**) no Visual Studio.

2. Marque a caixa de seleção **contadores do .net** .

   :::image type="content" source="../profiling/media/dotnet-counters-tool-selected.png" alt-text="Ferramenta de contadores selecionada.":::

3. Clique no botão **Iniciar** para executar a ferramenta.

Para obter mais informações sobre como otimizar o desempenho da ferramenta, consulte [otimizando as configurações do criador de perfil](../profiling/optimize-profiler-settings.md).


## <a name="understand-your-data"></a>Entenda seus dados

Embora a ferramenta esteja coletando dados inicialmente, você pode ver os valores dinâmicos dos [contadores dotnet](/dotnet/core/diagnostics/dotnet-counters).

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text="Ferramenta de contador .NET coletando.":::

Você também pode exibir grafos dos contadores marcando a caixa de seleção ao lado dos nomes dos contadores. Você pode exibir os gráficos de vários contadores de cada vez.


Depois de concluir o exercício de seu aplicativo e coletar dados, você pode interromper a coleta para um relatório ainda mais detalhado. Para fazer isso, pressione o botão **parar coleção** .


Depois que o relatório for carregado, você deverá ver um relatório finalizado semelhante ao mostrado abaixo.

:::image type="content" source="../profiling/media/dotnet-counters-tool-report.png" alt-text="Relatório da ferramenta de contador do .NET.":::

O relatório mostra os seguintes valores:

- Min-o valor mínimo para esse contador no intervalo de tempo selecionado.
- Max – o valor máximo para esse contador no intervalo de tempo selecionado.
- Média – o valor médio para esse contador no intervalo de tempo selecionado.

Você pode filtrar ou adicionar colunas na tabela clicando com o botão direito do mouse nos títulos das colunas e selecionando um título.

:::image type="content" source="../profiling/media/dotnet-counters-tool-columns.png" alt-text="Colunas da ferramenta do contador do .NET.":::

Você também pode exibir grafos no relatório detalhado selecionando as caixas de seleção ao lado de contadores. Os dados nas tabelas representam os valores de toda a duração do seu rastreamento coletado por padrão. Para filtrar os dados em um intervalo de tempo específico, clique e arraste os gráficos.

:::image type="content" source="../profiling/media/dotnet-counters-tool-time-filtering.png" alt-text="Filtragem de tempo da ferramenta de contadores do .NET.":::

A tabela é atualizada para valores relevantes para o tempo selecionado nos grafos. Use o botão **limpar seleção** para redefinir o intervalo de tempo selecionado para o rastreamento inteiro.


## <a name="see-also"></a>Veja também

- [Otimizando as configurações do criador de perfil](../profiling/optimize-profiler-settings.md)
- [contadores dotnet](/dotnet/core/diagnostics/dotnet-counters)
