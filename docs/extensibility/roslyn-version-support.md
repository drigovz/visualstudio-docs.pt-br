---
title: Mapeamentos de versão do pacote de Roslyn com suporte
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3b2dd97b078923cfa3358d56e6316bfff654c4dd
ms.sourcegitcommit: 62f42113ae4dae1ddfff1c4e02445acc09913445
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64878233"
---
# <a name="net-compiler-platform-package-version-reference"></a>Referência de versão de pacote de plataforma do .NET compilador

A tabela a seguir mostra quais [pacote de plataforma (Roslyn) do compilador .NET](https://www.nuget.org/packages/Microsoft.Net.Compilers/) versões têm suporte para versões diferentes do Visual Studio.

Por exemplo, para garantir que o seu analisador personalizada funciona em todas as versões do Visual Studio 2017, ele deve ter como destino a versão 2.0 do compilers.

| Versão do pacote de Roslyn | Visual Studio versão mínima com suporte |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 versão 15,9 |
| 2.9.0 | Visual Studio 2017 versão 15.8 |
| 2.8.2 | Visual Studio 2017 versão 15.7 |
| 2.7.0 | Visual Studio 2017 versão 15.6 |
| 2.6.1 | Visual Studio 2017 versão 15.5 |
| 2.4.0 | Visual Studio 2017 versão 15.4 |
| 2.3.2 | Visual Studio 2017 versão 15.3 |
| 2.2.0 | Visual Studio 2017 versão 15.2 |
| 2.1.0 | Visual Studio 2017 versão 15.1 |
| 2.0.0 | Visual Studio 2017 RTM |
| 1.3.2 | Visual Studio 2015 atualização 3 |
| 1.2.2 | Visual Studio 2015 atualização 2 |
| 1.1.1 | Visual Studio 2015 atualização 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> Para pacotes de Roslyn em que a versão mínima com suporte do Visual Studio é uma versão do Visual Studio 2017, também há suporte para todas as versões do Visual Studio de 2019 porque eles vieram mais tarde.

## <a name="see-also"></a>Consulte também

- [SDK do .NET Compiler Platform](/dotnet/csharp/roslyn-sdk/)
- [Introdução ao analisadores Roslyn](getting-started-with-roslyn-analyzers.md)