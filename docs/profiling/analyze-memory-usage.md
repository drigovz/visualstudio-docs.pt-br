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
ms.openlocfilehash: 124b792e134b31a5964c8f202c7870a58bc0878b
ms.sourcegitcommit: 53bc4c11b82882ab658e34c65ae374060f823531
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71128244"
---
# <a name="analyze-memory-usage"></a>Analisar o uso de memória
Use a ferramenta de diagnóstico **Uso de Memória** integrada no depurador para localizar perdas de memória e uso de memória ineficiente. A ferramenta Uso de Memória permite que você tire um ou mais *instantâneos* do heap de memória gerenciada e do heap de memória nativa. Você pode coletar instantâneos de aplicativos .NET, ASP.NET, nativos ou mistos (.NET e nativos).

- É possível analisar um único instantâneo para compreender o impacto relativo dos tipos de objeto sobre o uso da memória e encontrar o código no aplicativo que usa a memória de maneira ineficiente.

- Também é possível comparar (diff) dois instantâneos de um aplicativo para encontrar áreas no código que causam o aumento do uso da memória com o passar do tempo.

Para obter instruções detalhadas, consulte o tutorial [Analisar o uso de memória](../profiling/memory-usage.md).  Atualmente, para medir o uso de memória de um aplicativo .NET Core, é necessário usar a ferramenta com o depurador anexado. Para outros aplicativos gerenciados e nativos, é possível usar a ferramenta com ou sem o depurador anexado.

Você pode usar as ferramentas de criação de perfil sem o depurador com o Windows 7 e posteriores. O Windows 8 ou posterior é necessário para executar ferramentas de criação de perfil com o depurador (janela **Ferramentas de Diagnóstico**).

## <a name="blogs-and-videos"></a>Blogs e vídeos

[Analisar a CPU e a memória durante a depuração](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Blog do Visual C++: Criação de perfil de memória no Visual C++ 2015](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="see-also"></a>Consulte também

- [Criação de perfis no Visual Studio](../profiling/index.yml)
- [Introdução às ferramentas de criação de perfil](../profiling/profiling-feature-tour.md)