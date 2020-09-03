---
title: Introdução com analisadores Roslyn | Microsoft Docs
ms.date: 04/02/2018
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc975ff4f142b85297c20f16ac399fce588c093b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711266"
---
# <a name="get-started-with-roslyn-analyzers"></a>Introdução aos analisadores do Roslyn

Com o Live, analisadores de código baseados em projeto no Visual Studio, os autores de API podem enviar análises de código específicas de domínio como parte de seus pacotes NuGet. Como esses analisadores são alimentados pelo .NET Compiler Platform (codinome "Roslyn"), eles podem produzir avisos em seu código à medida que você digita, mesmo antes de terminar a linha (não mais esperando para criar seu código para descobrir problemas). Os analisadores também podem trazer uma correção automática de código por meio do prompt de lâmpada do Visual Studio para permitir que você limpe seu código imediatamente.

## <a name="get-started"></a>Introdução

[Visão geral dos analisadores do Roslyn](../code-quality/roslyn-analyzers-overview.md)

[Tutorial: escrever seu primeiro analisador e correção de código](/dotnet/csharp/roslyn-sdk/tutorials/how-to-write-csharp-analyzer-code-fix)

[Adicionar o Code fixes Walkthrough: fornecer correções de usuários para problemas do Analyzer](https://msdn.microsoft.com/magazine/dn904670.aspx)

O [Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , que você também pode assistir como uma [palestra](https://channel9.msdn.com/events/Build/2015/3-725)

[Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

## <a name="see-also"></a>Confira também

- [Referência de versão do pacote da plataforma de compilador .NET](roslyn-version-support.md)
- [Mais documentos no site de OSS do GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
- [Regras do FxCop implementadas com analisadores Roslyn](../code-quality/fxcop-rule-port-status.md)
