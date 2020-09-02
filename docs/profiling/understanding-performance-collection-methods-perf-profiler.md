---
title: Entender os métodos de coleta de desempenho do criador de perfil
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f0e24f3fc33ea456ad02bf9797b934a1a56d4492
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88238576"
---
# <a name="understand-profiler-performance-collection-methods"></a>Entender os métodos de coleta de desempenho do criador de perfil

Este documento descreve os métodos de coleta de dados que as ferramentas do criador de perfil de desempenho do Visual Studio utilizam. 

## <a name="sampling"></a>amostragem

Os métodos de amostragem para a criação de perfil coletam dados estatísticos sobre o trabalho que é executado por um aplicativo durante uma execução de criação de perfil. A coleta de dados é feita coletando informações sobre o aplicativo em um intervalo regular ou uma frequência de amostragem, como a cada milissegundo e, em seguida, analisando esses dados para criar um modelo de onde o tempo foi gasto no aplicativo. O método de amostragem é leve e tem pouco efeito sobre a execução do aplicativo que está sendo criado para o perfil. As ferramentas no criador de perfil de desempenho que utilizam o método de amostragem incluem a ferramenta de [uso da CPU](../profiling/cpu-usage.md) .

## <a name="instrumentation"></a>Instrumentação

A criação de perfil de instrumentação coleta informações detalhadas sobre o trabalho que é executado por um aplicativo durante uma execução de criação de perfil. A coleta de dados é feita por ferramentas que inserem código em um arquivo binário que captura informações de tempo ou usando ganchos de retorno de chamada para coletar e emitir informações exatas de tempo e contagem de chamadas durante a execução de um aplicativo. O método de instrumentação tem uma alta sobrecarga quando comparado às abordagens baseadas em amostragem. As ferramentas no criador de perfil de desempenho que usam a instrumentação incluem a ferramenta de [alocação de objeto .net](../profiling/dotnet-alloc-tool.md) .