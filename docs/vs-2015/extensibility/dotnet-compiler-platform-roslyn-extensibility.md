---
title: Extensibilidade de .NET Compiler Platform ( &quot; Roslyn &quot; ) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 564201b3-1e18-4b88-b615-42c2f57f3fe8
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fba277731444a294f276f43cc67b098039f4a64f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204727"
---
# <a name="net-compiler-platform-quotroslynquot-extensibility"></a>Extensibilidade do .NET Compiler Platform (&quot;Roslyn&quot;)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A missão principal do .NET Compiler Platform ("Roslyn") é abrir os compiladores do C# e do Visual Basic e permitir que ferramentas e desenvolvedores compartilhem nos compiladores de informações ricas sobre programas. As ferramentas de análise de código melhoram a qualidade do código e os geradores de código auxiliam na construção do aplicativo. Como as ferramentas são mais inteligentes, elas precisam acessar cada vez mais o conhecimento de código profundo que apenas os compiladores possuem. Em vez de serem tradutores opacos (código-fonte no e código do objeto), os compiladores do Roslyn oferecem APIs que você pode usar para tarefas relacionadas a código em suas ferramentas e aplicativos.  
  
 A melhor parte é que os compiladores do Roslyn, suas APIs, exemplos e instruções passo a passos, e as ferramentas reais criadas com base nessas APIs são totalmente abertas em [github.com/dotnet/Roslyn](https://github.com/dotnet/Roslyn). Acesse o site do OSS para saber mais e comece a usar o Roslyn. Você encontrará links para obter os recursos mais recentes do C# e do VB que podem ser usados como um usuário final, bem como links para começar como um construtor de ferramentas, aproveitando as APIs do Roslyn.  
  
## <a name="see-also"></a>Consulte Também  
 [Introdução aos analisadores Roslyn](../extensibility/getting-started-with-roslyn-analyzers.md)
