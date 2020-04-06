---
title: Mapeamentos de versão do pacote Roslyn suportados
ms.date: 04/29/2019
ms.topic: reference
helpviewer_keywords:
- roslyn package versions
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1dd268dadd03ee5d648075ccea1763e949719c90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701330"
---
# <a name="net-compiler-platform-package-version-reference"></a>Referência da versão do pacote da plataforma .NET

A tabela a seguir mostra quais versões [do pacote .NET compiler platform (Roslyn)](https://www.nuget.org/packages/Microsoft.Net.Compilers/) são suportadas para diferentes versões do Visual Studio.

Como exemplo, para garantir que seu analisador personalizado funcione em todas as versões do Visual Studio 2017, ele deve ter como alvo a versão 2.0 do Microsoft.Net.Compilers.

| Versão do pacote roslyn | Versão visual studio suportada mínima |
| - | - |
| 3.x | Visual Studio 2019 |
| 2.10.0 | Visual Studio 2017 versão 15.9 |
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
> Para os pacotes roslyn onde a versão visual studio suportada mínima é uma versão visual studio 2017, todas as versões do Visual Studio 2019 também são suportadas porque vieram mais tarde.

## <a name="see-also"></a>Confira também

- [SDK da Plataforma do Compilador .NET](/dotnet/csharp/roslyn-sdk/)
- [Comece com os analisadores roslyn](getting-started-with-roslyn-analyzers.md)
