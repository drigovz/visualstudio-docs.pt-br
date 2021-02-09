---
title: API de gráficos e estatísticas de memória | Microsoft Docs
description: Examine as ferramentas estatísticas de API de gráficos e estatísticas de memória, que mostram informações sobre o uso da API do Direct3D e o consumo de memória de GPU de vários recursos.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 08c9f518f6d56f2ec211ef494da3890a56bf1369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882291"
---
# <a name="graphics-api-and-memory-statistics"></a>Estatísticas de memória e API de gráficos
<!-- VERSIONLESS -->
O Visual Studio 2017 e superior dá suporte às ferramentas estatísticas de API de gráficos e estatísticas de memória.  Essas duas ferramentas permitem exibir vários bits de informações sobre o uso da API do Direct3D, bem como o consumo de memória da GPU de vários recursos.

## <a name="graphics-api-statistics"></a>Estatísticas de API de gráficos
As estatísticas de API de gráficos no Visual Studio Diagnóstico de Gráficos permitem exibir todas as chamadas de Direct3D que foram feitas e a contagem de cada chamada.  Para exibir a janela, selecione o item de menu **exibir > estatísticas de API** .

![Estatísticas de API](media/gfx_diag_api_statistics.png)

Essa ferramenta pode ser útil para descobrir chamadas do DirectX que você talvez não perceba, ou chamadas que você está fazendo com muita frequência.

Você pode clicar com o botão direito do mouse na janela para copiar todos os dados como CSV, que podem ser colados em algo como o Excel para análise posterior.

## <a name="memory-statistics"></a>Estatísticas de Memória
Essa ferramenta exibirá a quantidade de memória que o driver de gráficos está alocando para os recursos que você criar em um quadro.  Para exibir essa janela, selecione o item de menu **exibir > estatísticas de memória** .

![Estatísticas de Memória](media/gfx_diag_memory_statistics.png)

A coluna **alocação de GPU** exibe a quantidade de memória usada pelo evento exibido na coluna **evento** .  Você também pode selecionar o ícone de inspeção ícone de inspeção ![ ](media/gfx_watch.png) para exibir o [histórico de recursos](graphics-event-list.md#resource-history) do evento selecionado.

Assim como acontece com a ferramenta de estatísticas de API, você pode clicar com o botão direito do mouse na janela para copiar todos os dados como CSV, que podem ser colados em algo como o Excel para análise posterior.

## <a name="see-also"></a>Confira também
- [Diagnóstico de gráficos (depuração de gráficos DirectX)](visual-studio-graphics-diagnostics.md)
- [Histórico de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->