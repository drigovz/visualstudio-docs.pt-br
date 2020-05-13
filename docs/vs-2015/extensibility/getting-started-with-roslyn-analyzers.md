---
title: Começando com Roslyn Analyzers | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a712697bafefcf115ce10d110c0ef3a4270c6acd
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444958"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introdução aos analisadores Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com analisadores de código ao vivo e baseados em projetos no Visual Studio, os autores da API podem enviar análises de código específicas de domínio como parte de seus pacotes NuGet.  Como esses analisadores são alimentados pela Plataforma de Compilador .NET (codinome "Roslyn"), eles podem produzir avisos em seu código à medida que você digita antes mesmo de terminar a linha (não há mais espera para construir seu código para descobrir problemas).  Os analisadores também podem fazer uma correção automática de código através do aviso de lâmpada do Visual Studio para permitir que você limpe seu código imediatamente

## <a name="getting-started"></a>Introdução
[Roslyn Live Code Analyzers Introdução e Passo a Passo](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Adicionando correções de código passo a passo: forneça aos usuários correções para problemas do analisador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introdução e Walkthrough do Real World Analyzer Talk](https://channel9.msdn.com/events/Build/2015/3-725)

[Real World Roslyn Analyzer](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que você também pode assistir como uma [palestra](https://channel9.msdn.com/events/Build/2015/3-725)

[Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introdução e Tour de um Poucos Analisadores Talk](https://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Outros recursos
[Mais docs no site do GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Regras do FxCop implementadas com analisadores Roslyn no GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
