---
title: Avaliação de tempo de execução e expressão de linguagem comum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 013579473189dd9310501b76d2de0d5cf6fa5822
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739116"
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Avaliação de tempo de execução e expressão de linguagem comum
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Compiladores, como Visual Basic e C# (pronuncia-se C-sharp), que têm como alvo o Common Language Runtime (CLR), produzem o Microsoft Intermediate Language (MSIL), que é posteriormente compilado para código nativo. O CLR fornece um mecanismo de depuração (DE) para depurar o código resultante. Se você planeja integrar sua linguagem de programação proprietária ao Visual Studio IDE, você pode optar por compilar para o MSIL e, portanto, não terá que escrever seu próprio DE. No entanto, você terá que escrever um avaliador de expressão (EE) capaz de avaliar expressões dentro do contexto de sua linguagem de programação.

## <a name="discussion"></a>Discussão
 As expressões de linguagem de computador são geralmente analisados para produzir um conjunto de objetos de dados e um conjunto de operadores usados para manipulá-los. Por exemplo, a expressão "A+B" pode ser analisado para aplicar o operador de adição (+) aos objetos de dados "A" e "B", possivelmente resultando em outro objeto de dados. O conjunto total de objetos de dados, operadores e suas associações são mais frequentemente representados em um programa como uma árvore, com os operadores nos nós da árvore e os objetos de dados nos galhos. Uma expressão que foi dividida em forma de árvore é muitas vezes chamada de árvore parsed.

 Uma vez que uma expressão é analisado, um provedor de símbolos (SP) é chamado para avaliar cada objeto de dados. Por exemplo, se "A" for definido tanto em mais de um método, a pergunta "Qual A?" deve ser respondida antes que o valor de A possa ser apurado. A resposta devolvida pelo SP é algo como "O terceiro item no quadro da quinta pilha" ou "O A que é de 50 bytes além do início da memória estática atribuída a este método".

 Além de produzir MSIL para o programa em si, os compiladores CLR também podem produzir informações de depuração muito descritivas que são escritas em um arquivo Program DataBase (*.pdb).* Enquanto um compilador de idioma proprietário produz informações depuradas no mesmo formato que os compiladores CLR, o CONTROLADOR da CLR é capaz de identificar os objetos de dados nomeados dessa linguagem. Uma vez identificado um objeto de dados nomeado, o EE usa um objeto de encadernação para associar (ou vincular) o objeto de dados à área de memória que contém o valor desse objeto. O DE pode então obter ou definir um novo valor para o objeto de dados.

 Um compilador proprietário pode fornecer informações de depuração CLR ligando para a `ISymbolWriter` interface `System.Diagnostics.SymbolStore`(que é definida no .NET Framework no namespace ). Ao compilar para o MSIL e escrever informações de depuração através dessas interfaces, um compilador proprietário pode usar o CLR DE e sp. Isso simplifica muito a integração de uma linguagem proprietária no Visual Studio IDE.

 Quando o CLR DE chama o EE proprietário para avaliar uma expressão, o DE fornece ao EE interfaces para uma SP e um objeto de encadernação. Assim, escrever um mecanismo de depuração baseado em CLR significa que é necessário apenas implementar as interfaces de avaliador de expressão apropriadas; a CLR cuida da ligação e do manuseio do símbolo para você.

## <a name="see-also"></a>Confira também
- [Escreva um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
