---
title: Analisar o uso de memória
ms.custom: seodec18
ms.date: 01/02/2018
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 43126f4bba8afc50fc5c1e4cf6a3b9a67c6f340c
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80233056"
---
# <a name="analyze-memory-usage"></a>Analisar o uso de memória

para encontrar vazamentos de memória e uso ineficiente de memória, você pode usar ferramentas como a ferramenta de diagnóstico de uso de memória integrada ao depurador ou ferramentas no Profiler de desempenho, como a ferramenta .NET Object Allocation e a ferramenta post-mortem Memory Use.

A ferramenta Uso de Memória permite que você tire um ou mais *instantâneos* do heap de memória gerenciada e do heap de memória nativa. Você pode coletar instantâneos de aplicativos .NET, ASP.NET, nativos ou mistos (.NET e nativos). A ferramenta **Uso de memória** pode ser executada em um projeto aberto do Visual Studio, em um aplicativo da Microsoft Store instalado ou conectado a um aplicativo ou processo em execução. É possível executar a ferramenta em computadores locais ou remotos ou em um simulador ou emulador. Você pode executar a ferramenta **Uso de memória** com ou sem depuração. Para obter mais informações, consulte [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). No depurador, você pode ativar e desativar o perfil de memória e ver uma quebra por objeto do uso da memória. Você pode visualizar os resultados de uso da memória quando a execução é pausada, por exemplo, em um ponto de ruptura.

A ferramenta **.NET Object Allocation** ajuda a identificar padrões de alocação e anomalias em seu código .NET. Esta ferramenta funciona apenas como uma ferramenta post-mortem.

Para obter instruções detalhadas que descrevam como usar as ferramentas de análise de memória, consulte o tutorial [de uso de memória Analyze](../profiling/memory-usage.md) e a ferramenta [.NET Object Allocation](../profiling/dotnet-alloc-tool.md).

Você pode usar as ferramentas de criação de perfil sem o depurador com o Windows 7 e posteriores. O Windows 8 ou posterior é necessário para executar ferramentas de criação de perfil com o depurador (janela **Ferramentas de Diagnóstico**).

## <a name="blogs-and-videos"></a>Blogs e vídeos

[Analisar cpu e memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Perfil de memória no Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Confira também

- [Criação de perfis no Visual Studio](../profiling/index.yml)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)
- [Analisar o uso de memória sem o depurador](../profiling/memory-usage-without-debugging2.md)
