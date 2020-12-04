---
title: Habilitar ou instalar analisadores de .NET de primeira empresa
ms.date: 08/03/2018
description: Saiba como habilitar os analisadores de .NET de primeira empresa no SDK do .NET ou instalar esses analisadores como um pacote NuGet.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- .NET analyzers
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 60eb4828d4c8450376178c2fdccf7d4c0f63d989
ms.sourcegitcommit: 208bd1edebfe6dec5d3bb92c63b5c1e093677e35
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96440369"
---
# <a name="enable-or-install-first-party-net-analyzers"></a>Habilitar ou instalar analisadores de .NET de primeira empresa

## <a name="overview"></a>Visão geral

Os analisadores do .NET Compiler Platform (Roslyn) inspecionam código em C# ou no Visual Basic em busca de problemas de estilo e de qualidade. Você pode habilitar ou instalar os analisadores de .NET primários de uma das seguintes maneiras:

- **Habilitar do SDK do .net**: a partir do Visual Studio 2019 16,8 e do .NET 5,0, esses analisadores estão [incluídos no SDK do .net](/dotnet/fundamentals/code-analysis/overview). A análise é habilitada, por padrão, para projetos direcionados ao .NET 5,0 ou posterior. Você pode habilitar a análise de código em projetos direcionados a versões anteriores do .NET definindo a `EnableNETAnalyzers` propriedade como `true` . Você também pode desabilitar a análise de código para seu projeto definindo `EnableNETAnalyzers` como `false` .

- **Instalar como um pacote NuGet**: como alternativa, você pode instalar esses analisadores instalando o `Microsoft.CodeAnalysis.NetAnalyzers` [pacote nuget](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers) no Visual Studio 2019. Se você estiver no Visual Studio 2017, instale a versão mais recente `2.9.x` do `Microsoft.CodeAnalysis.FxCopAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/).

> [!NOTE]
> É recomendável que você habilite os analisadores do SDK do .NET em vez de instalar o `Microsoft.CodeAnalysis.NetAnalyzers` [pacote NuGet](https://www.nuget.org/packages/Microsoft.CodeAnalysis.NetAnalyzers), quando possível. Habilitar os analisadores do SDK do .NET garante que você obtenha automaticamente as correções de bugs do analisador e novos analisadores assim que atualizar o SDK.

## <a name="see-also"></a>Confira também

- [Visão geral dos analisadores de código no Visual Studio](roslyn-analyzers-overview.md)
- [Usar analisadores de código no Visual Studio](use-roslyn-analyzers.md)
- [Migrar da análise herdada para analisadores de .NET](migrate-from-legacy-analysis-to-net-analyzers.md)
- [Migrar de analisadores do FxCop para analisadores de .NET](migrate-from-fxcop-analyzers-to-net-analyzers.md)