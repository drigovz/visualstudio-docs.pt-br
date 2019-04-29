---
title: API de gráficos e estatísticas de memória | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.apistatistics
- vs.graphics.memorystatistics
ms.assetid: 27d2f303-e3ed-4219-9009-345a0d849506
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7810889d4af411477573c71aa694d797a90763f3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62896013"
---
# <a name="graphics-api-and-memory-statistics"></a>API de gráficos e estatísticas de memória
<!-- VERSIONLESS -->
Visual Studio 2017 e maior suporte a estatísticas de API de gráficos e ferramentas de estatísticas de memória.  Essas duas ferramentas permitem que você exiba vários bits de informação no uso da API do Direct3D, bem como o consumo de memória GPU de vários recursos.

## <a name="graphics-api-statistics"></a>Estatísticas de API de gráficos
As estatísticas de API de gráficos no diagnóstico de gráficos do Visual Studio permite que você exiba todas as chamadas Direct3D que foram feitas e a contagem de cada chamada.  Para exibir a janela, selecione a **Exibir > estatísticas de API** item de menu.

![Estatísticas de API](media/gfx_diag_api_statistics.png)

Essa ferramenta pode ser útil em descobrir a chamadas DirectX que talvez não percebam estamos fazendo ou chamadas que você está fazendo com muita frequência.

Você pode clique com botão direito na janela para copiar todos os dados como CSV, que pode ser colado em algo parecido com o Excel para análise posterior.

## <a name="memory-statistics"></a>Estatísticas de Memória
Essa ferramenta exibirá a quantidade de memória do driver de gráficos está alocando para os recursos que você cria em um quadro.  Para exibir essa janela, selecione a **Exibir > estatísticas de memória** item de menu.

![Estatísticas de Memória](media/gfx_diag_memory_statistics.png)

O **alocação de GPU** coluna exibe a quantidade de memória usada pelo evento exibido na **evento** coluna.  Você também pode selecionar o ícone de inspeção ![ícone de inspeção](media/gfx_watch.png) para exibir o [histórico de recursos](graphics-event-list.md#resource-history) para o evento selecionado.

Assim como acontece com a ferramenta de estatísticas de API, você pode clique com botão direito na janela para copiar todos os dados como CSV, que pode ser colado em algo parecido com o Excel para análise posterior.

## <a name="see-also"></a>Consulte também
- [Diagnóstico de gráficos (depuração de gráficos DirectX)](visual-studio-graphics-diagnostics.md)
- [Histórico de recursos](graphics-event-list.md#resource-history)
<!-- /VERSIONLESS -->