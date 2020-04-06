---
title: .NET Compiler&quot;Platform&quot;(Roslyn ) Extensibility | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 62ceac6e2be8a0a84d82f6b86b685c7c8b20a182
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712075"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>.NET Compiler&quot;Platform&quot;(Roslyn ) extensibilidade
A missão central da Plataforma de Compiladores .NET ("Roslyn") é abrir os compiladores C# e Visual Basic e permitir que ferramentas e desenvolvedores compartilhem as ricas informações que os compiladores têm sobre programas. Ferramentas de análise de código melhoram a qualidade do código, e geradores de código ajudam na construção de aplicativos. À medida que as ferramentas ficam mais inteligentes, elas precisam de acesso a cada vez mais conhecimento de código profundo que só os compiladores possuem. Em vez de serem tradutores opacos (código fonte e código de objeto eliminado), os compiladores Roslyn oferecem APIs que você pode usar para tarefas relacionadas ao código em suas ferramentas e aplicativos.

 A melhor parte é que os compiladores roslyn, suas APIs, amostras e passo a passo, e as ferramentas reais construídas em cima dessas APIs são todas totalmente de código aberto em [github.com/dotnet/roslyn](https://github.com/dotnet/Roslyn). Por favor, vá para o site da OSS para saber mais e começar com Roslyn. Você encontrará links para obter os recursos mais recentes C# e Visual Basic que você pode usar como usuário final, bem como links para começar como um construtor de ferramentas aproveitando as APIs roslyn.

## <a name="see-also"></a>Confira também
- [Comece com os analisadores roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
