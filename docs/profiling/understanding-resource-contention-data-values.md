---
title: Noções Básicas sobre valores de dados de contenção de recurso | Microsoft Docs
description: Saiba como a criação de perfil de contenção de recursos coleta informações detalhadas quando threads concorrentes em um aplicativo são forçados a aguardar o acesso a um recurso compartilhado.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- concurrency profiling method
- Profiling Tools, concurrency method
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1a724c360641926bcb64552f6f26e92d3c524011
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722198"
---
# <a name="understand-resource-contention-data-values"></a>Noções básicas sobre valores de dados de contenção de recurso

Perfis de contenção de recursos coletam informações de pilha de chamadas detalhadas sempre que segmentos concorrentes em um aplicativo são forçados a aguardar o acesso a um recurso compartilhado.

Relatórios de contenção do recurso exibem o número total de contenções e o tempo total gasto aguardando um recurso para os módulos, funções, linhas de código-fonte e instruções no qual ocorreu a espera.

- Valores inclusivos exibem o número total de contenções que forçou uma função a espera por contenção de recursos e o tempo total que a função esperou.  Contenções que foram causadas por funções filho que foram chamadas pela função são incluídas nos valores inclusivos.

- Valores exclusivos exibem apenas o número de contenções que forçaram uma função a esperar e que foram causadas pelo código no corpo da função. Contenções causadas por funções filho não são incluídas. O tempo exclusivo para a função também inclui somente os tempos de espera que foram causados por instruções no corpo da função.

Exibições de relatório de contenção de recursos também incluem gráficos de linha do tempo que mostram os eventos de contenção individuais ao longo do tempo e mostram as pilhas de chamadas que criaram o evento específico. Para obter mais informações, consulte um dos tópicos a seguir.

- [Exibição de detalhes do thread](../profiling/thread-details-view-contention-data.md)

- [Exibição de detalhes do recurso](../profiling/resource-details-view-contention-data.md)

Para obter mais informações sobre o segundo modo de criação de perfil de simultaneidade, consulte [Visualização Simultânea](../profiling/concurrency-visualizer.md).
