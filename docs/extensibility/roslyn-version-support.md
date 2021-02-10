---
title: Mapeamentos de versão do pacote Roslyn com suporte
description: Este artigo mostra quais versões de pacote do Roslyn (plataforma de compilador .NET) têm suporte para diferentes versões do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f76a8dcdbb644fe456c62fca7de6fb7afe96d556
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935878"
---
# <a name="net-compiler-platform-package-version-reference"></a>Referência de versão do pacote da plataforma de compilador .NET

A tabela a seguir mostra quais versões de [pacote do Roslyn (plataforma de compilador .net)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) têm suporte para versões diferentes do Visual Studio.

Por exemplo, para garantir que o analisador personalizado funcione em todas as versões do Visual Studio 2017, ele deve ter como destino a versão 2,0 do Microsoft.Net. compilers.

| Versão do pacote Roslyn | Versão mínima do Visual Studio com suporte |
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
| 1.3.2 | Atualização 3 do Visual Studio 2015 |
| 1.2.2 | Atualização 2 do Visual Studio 2015 |
| 1.1.1 | Visual Studio 2015 atualização 1 |
| 1.0.1 | Visual Studio 2015 RTM |

> [!TIP]
> Para pacotes Roslyn em que a versão mínima com suporte do Visual Studio é uma versão do Visual Studio 2017, todas as versões do Visual Studio 2019 também têm suporte porque foram fornecidas mais tarde.

## <a name="see-also"></a>Confira também

- [SDK da Plataforma do Compilador .NET](/dotnet/csharp/roslyn-sdk/)
- [Introdução aos analisadores do Roslyn](getting-started-with-roslyn-analyzers.md)
