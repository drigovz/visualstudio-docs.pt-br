---
title: Introdução ao analisadores Roslyn | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 367c2ec8-3059-46a5-9d1c-57bead0419e7
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 104e3a30589f5892c1440266afd7917486d704ec
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58924842"
---
# <a name="getting-started-with-roslyn-analyzers"></a>Introdução aos analisadores Roslyn
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Com os analisadores de código ao vivo, com base em projeto no Visual Studio, os autores do API podem ser fornecidas a análise de código específica de domínio como parte de seus pacotes NuGet.  Porque desses analisadores serem alimentados pela plataforma do compilador .NET (cujo codinome é "Roslyn"), eles podem produzir alertas em seu código enquanto você digita, mesmo antes de terminar a linha (não precisa mais esperar para compilar seu código para descobrir problemas).  Os analisadores também podem surgir uma correção automática de código por meio do prompt de lâmpada do Visual Studio para deixá-lo limpar seu código imediatamente

## <a name="getting-started"></a>Guia de Introdução
[Analisadores de código em tempo real do Roslyn Introdução e instruções passo a passo](https://msdn.microsoft.com/magazine/dn879356.aspx)

[Adicionando código corrige o passo a passo: Fornecer usuários correções para problemas de analisador](https://msdn.microsoft.com/magazine/dn904670.aspx)

[Introdução e instruções passo a passo da palestra de analisador do mundo Real](http://channel9.msdn.com/events/Build/2015/3-725)

[Analisador de Roslyn de mundo real](../extensibility/roslyn-analyzers-and-code-aware-library-for-immutablearrays.md) que você também pode assistir como um [falar](http://channel9.msdn.com/events/Build/2015/3-725)

[Vários exemplos no GitHub, agrupados em três tipos de analisadores](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)

[Introdução e Tour alguns analisadores falar](http://channel9.msdn.com/Events/dotnetConf/2015/NET-Compiler-Platform-Roslyn-Analyzers-and-the-Rise-of-Code-Aware-Libraries)

## <a name="other-resources"></a>Outros recursos
[Docs mais no site do GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)

[Regras do FxCop implementadas com analisadores de Roslyn no GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
