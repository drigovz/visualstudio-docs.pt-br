---
title: Começando com Roslyn Analyzers | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711266"
---
# <a name="get-started-with-roslyn-analyzers"></a>Comece com os analisadores roslyn

Com analisadores de código ao vivo e baseados em projetos no Visual Studio, os autores da API podem enviar análises de código específicas de domínio como parte de seus pacotes NuGet. Como esses analisadores são alimentados pela Plataforma de Compilador .NET (codinome "Roslyn"), eles podem produzir avisos em seu código à medida que você digita antes mesmo de terminar a linha (não há mais espera para construir seu código para descobrir problemas). Os analisadores também podem fazer uma correção automática de código através do aviso de lâmpada do Visual Studio para permitir que você limpe seu código imediatamente.

## <a name="get-started"></a>Introdução

[Análiseres roslyn visão geral](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: escrever seu primeiro analisador e correção de código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Adicionar correções de código Passo a passo: forneça aos usuários correções para problemas do analisador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Analisador roslyn do mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que você também pode assistir como uma [palestra](https://channel9.msdn.com/events/Build/2015/3-725)

[Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Confira também

- [Referência da versão do pacote da plataforma .NET](roslyn-version-support.md)
- [Mais docs no site do GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regras da FxCop implementadas com analisadores Roslyn](../code-quality/fxcop-rule-port-status.md)
