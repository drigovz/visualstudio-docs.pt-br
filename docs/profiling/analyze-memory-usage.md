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
ms.openlocfilehash: 5ddb082bf2451759be239d5c16404e82bcd84733
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578166"
---
# <a name="analyze-memory-usage"></a>Analisar o uso de memória

para encontrar vazamentos de memória e uso ineficiente de memória, você pode usar ferramentas como a ferramenta de diagnóstico de uso de memória integrada do depurador ou ferramentas no criador de perfil de desempenho, como a ferramenta de alocação de objeto .NET e a ferramenta de uso de memória post-morte. A ferramenta Uso de Memória permite que você tire um ou mais *instantâneos* do heap de memória gerenciada e do heap de memória nativa. Você pode coletar instantâneos de aplicativos .NET, ASP.NET, nativos ou mistos (.NET e nativos). 

A ferramenta de **uso de memória** pode ser executada em um projeto aberto do Visual Studio, em um aplicativo Microsoft Store instalado ou anexado a um aplicativo ou processo em execução. É possível executar a ferramenta em computadores locais ou remotos ou em um simulador ou emulador. Para obter mais informações, confira [Executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Você pode executar a ferramenta de **uso de memória** com ou sem depuração. No depurador, você pode ativar e desativar a criação de perfil de memória e ver uma divisão por objeto de uso de memória. Você pode exibir os resultados de uso de memória quando a execução é pausada, por exemplo, em um ponto de interrupção.

A ferramenta de **alocação de objeto .net** é executada somente como uma ferramenta post-mortem.

Para obter instruções detalhadas que descrevem como usar as ferramentas de análise de memória, consulte o tutorial [analisar o uso de memória](../profiling/memory-usage.md) e a ferramenta de alocação de [objeto .net](../profiling/dotnet-alloc-tool.md).

Você pode usar as ferramentas de criação de perfil sem o depurador com o Windows 7 e posteriores. O Windows 8 ou posterior é necessário para executar ferramentas de criação de perfil com o depurador (janela **Ferramentas de Diagnóstico**).

## <a name="blogs-and-videos"></a>Blogs e vídeos

[Analisar a CPU e a memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog do Visual C++: Criação de perfil de memória no Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Confira também

- [Criação de perfis no Visual Studio](../profiling/index.yml)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)
- [Analisar o uso de memória sem o depurador](../profiling/memory-usage-without-debugging2.md)
