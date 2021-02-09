---
title: Entender os métodos de coleta de desempenho do criador de perfil
description: Saiba mais sobre os métodos de coleta de dados que as ferramentas do criador de perfil de desempenho do Visual Studio utilizam.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords: ''
helpviewer_keywords:
- Performance Profiler, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: '>= vs-2017'
ms.workload:
- multiple
ms.openlocfilehash: f9128700f6ad54f3d92108d92e25e13b9ee4266c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921867"
---
# <a name="understand-profiler-performance-collection-methods"></a>Entender os métodos de coleta de desempenho do criador de perfil

Este documento descreve os métodos de coleta de dados que as ferramentas do criador de perfil de desempenho do Visual Studio utilizam. 

## <a name="sampling"></a>amostragem

Os métodos de amostragem para a criação de perfil coletam dados estatísticos sobre o trabalho que é executado por um aplicativo durante uma execução de criação de perfil. A coleta de dados é feita coletando informações sobre o aplicativo em um intervalo regular ou uma frequência de amostragem, como a cada milissegundo e, em seguida, analisando esses dados para criar um modelo de onde o tempo foi gasto no aplicativo. O método de amostragem é leve e tem pouco efeito sobre a execução do aplicativo que está sendo criado para o perfil. As ferramentas no criador de perfil de desempenho que utilizam o método de amostragem incluem a ferramenta de [uso da CPU](../profiling/cpu-usage.md) .

## <a name="instrumentation"></a>Instrumentação

A criação de perfil de instrumentação coleta informações detalhadas sobre o trabalho que é executado por um aplicativo durante uma execução de criação de perfil. A coleta de dados é feita por ferramentas que inserem código em um arquivo binário que captura informações de tempo ou usando ganchos de retorno de chamada para coletar e emitir informações exatas de tempo e contagem de chamadas durante a execução de um aplicativo. O método de instrumentação tem uma alta sobrecarga quando comparado às abordagens baseadas em amostragem. As ferramentas no criador de perfil de desempenho que usam a instrumentação incluem a ferramenta de [alocação de objeto .net](../profiling/dotnet-alloc-tool.md) .