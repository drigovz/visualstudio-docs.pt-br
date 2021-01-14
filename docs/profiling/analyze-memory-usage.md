---
title: Analisar o uso de memória
description: Saiba mais sobre as ferramentas que você pode usar para encontrar vazamentos de memória e uso de memória ineficiente, ferramentas como a ferramenta de uso de memória e a ferramenta de alocação de objeto .NET.
ms.custom: SEO-VS-2020, seodec18
ms.date: 10/12/2020
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 675636b7abca10fb2f9f1898d753155235830f86
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205717"
---
# <a name="analyze-memory-usage"></a>Analisar o uso de memória

Para encontrar vazamentos de memória e uso ineficiente de memória, você pode usar ferramentas como a ferramenta de diagnóstico de uso de memória integrada do depurador ou ferramentas no criador de perfil de desempenho, como a ferramenta de alocação de objeto .NET e a ferramenta de uso de memória post-morte.

A ferramenta Uso de Memória permite que você tire um ou mais *instantâneos* do heap de memória gerenciada e do heap de memória nativa. Você pode coletar instantâneos dos aplicativos .NET, ASP.NET, C++ ou modo misto (.NET e nativo). A ferramenta de **uso de memória** pode ser executada em um projeto aberto do Visual Studio, em um aplicativo Microsoft Store instalado ou anexado a um aplicativo ou processo em execução. Você pode executar a ferramenta de **uso de memória** com ou sem depuração. Para obter mais informações, consulte [executar ferramentas de criação de perfil com ou sem o depurador](../profiling/running-profiling-tools-with-or-without-the-debugger.md). No depurador, você pode ativar e desativar a criação de perfil de memória e ver uma divisão por objeto de uso de memória. Você pode exibir os resultados de uso de memória quando a execução é pausada, por exemplo, em um ponto de interrupção.

Os desenvolvedores do .NET podem escolher entre a ferramenta de alocação de objeto .NET ou a ferramenta de [uso de memória](../profiling/memory-usage.md) .

- A [ferramenta de alocação de objeto .net](../profiling/dotnet-alloc-tool.md) ajuda a identificar padrões de alocação e anomalias em seu código .net e ajuda a identificar problemas comuns com a coleta de lixo. Essa ferramenta só é executada como uma ferramenta post-mortem. Você pode executar essa ferramenta em computadores locais ou remotos.
- A [ferramenta de uso de memória](../profiling/memory-usage-without-debugging2.md) é útil para identificar vazamentos de memória, que normalmente não são comuns em aplicativos .net. Se você precisar usar os recursos do depurador ao verificar a memória, como percorrer o código, a ferramenta de [uso de memória integrada ao depurador](../profiling/memory-usage.md) é recomendada.

Os desenvolvedores de C++ podem usar a ferramenta de uso de memória integrada ou não depurador.

- [Analisar o uso de memória com o depurador](../profiling/memory-usage.md)
- [Analisar o uso de memória sem o depurador](../profiling/memory-usage-without-debugging2.md)

Você pode usar as ferramentas de criação de perfil sem o depurador com o Windows 7 e posteriores. O Windows 8 ou posterior é necessário para executar ferramentas de criação de perfil com o depurador (janela **Ferramentas de Diagnóstico**).

## <a name="blogs-and-videos"></a>Blogs e vídeos

[Analisar CPU e memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog Visual C++: criação de perfil de memória no Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Confira também

- [Criação de perfis no Visual Studio](../profiling/index.yml)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)
