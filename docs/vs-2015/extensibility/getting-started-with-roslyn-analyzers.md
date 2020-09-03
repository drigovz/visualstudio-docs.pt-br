---
title: Introdução com analisadores Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "81444958"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introdução aos analisadores Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com o Live, analisadores de código baseados em projeto no Visual Studio, os autores de API podem enviar análises de código específicas de domínio como parte de seus pacotes NuGet.  Como esses analisadores são alimentados pelo .NET Compiler Platform (codinome "Roslyn"), eles podem produzir avisos em seu código à medida que você digita, mesmo antes de terminar a linha (não mais esperando para criar seu código para descobrir problemas).  Os analisadores também podem trazer uma correção automática de código por meio do prompt de lâmpada do Visual Studio para permitir que você limpe seu código imediatamente

## <a name="getting-started"></a>Introdução
[Introdução e instruções do Roslyn Live Code Analyzers](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Como adicionar correções de código explicando: fornecer correções aos usuários para problemas do Analyzer](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introdução e explicação do analisador do Real World Talk](https://channel9.msdn.com/events/Build/2015/3-725)

O [Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) , que você também pode assistir como uma [palestra](https://channel9.msdn.com/events/Build/2015/3-725)

[Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introdução e Tour de alguns analisadores falam](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Outros recursos
[Mais documentos no site de OSS do GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Regras do FxCop implementadas com analisadores Roslyn no GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
