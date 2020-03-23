---
title: Usar expressões regulares
ms.date: 09/13/2019
ms.topic: conceptual
f1_keywords:
- vsregularexpressionhelp
- vs.regularexpressionhelp
- vs.wildcardsbuilder
- vs.netregularexpressionhelp
- vs.wildcards
helpviewer_keywords:
- regular expressions [Visual Studio]
- regular expressions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1739d6b2376a4f86edd3c0102f7fad79da5d7cd
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568614"
---
# <a name="use-regular-expressions-in-visual-studio"></a>Usar expressões regulares no Visual Studio

O Visual Studio usa [expressões regulares .NET](/dotnet/standard/base-types/regular-expressions) para localizar e substituir texto.

## <a name="regular-expression-examples"></a>Exemplos de expressões regulares

A tabela a seguir contém alguns caracteres de expressão regular, operadores, constructos e exemplos de padrão. Para obter uma referência mais completa, confira [Linguagem de expressão regular](/dotnet/standard/base-types/regular-expression-language-quick-reference).

|Finalidade|Expression|Exemplo|
|-------------|----------------|-------------|
|Encontrar a correspondência de um único caractere (exceto uma quebra de linha). Para saber mais, veja [Qualquer caractere](/dotnet/standard/base-types/character-classes-in-regular-expressions#any-character-).|.|`a.o`corresponde "aro" em "ao redor" e "abo" em "cerca" mas não "acro" em "across"|
|Encontrar a correspondência de zero ou mais ocorrências da expressão anterior (encontrar a correspondência do máximo de caracteres possíveis). Para saber mais, confira [Corresponder a zero ou mais vezes](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-).|*|`a*r` corresponde a “r” em “rack”, “ar” em “ark” e “aar” em “aardvark”|
|Combine qualquer personagem zero ou mais vezes.|.*|`c.*e` corresponde a "cke" em "racket", "comme" em "comment" e "code" em "code"|
|Encontrar a correspondência de uma ou mais ocorrências da expressão anterior (encontrar a correspondência do máximo de caracteres possíveis). Para saber mais, confira [Corresponder a uma ou mais vezes](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-).|+|`e+d`corresponde "eed" em "feeder" e "ed" em "desbotado"|
|Corresponde qualquer caractere uma ou mais vezes.|.+|`e.+e`corresponde "eede" em "feeder", mas não encontra correspondências em "feed"|
|Encontrar a correspondência de zero ou mais ocorrências da expressão anterior (encontrar a correspondência do mínimo de caracteres possíveis). Para saber mais, confira [Corresponder a zero ou mais vezes (correspondência lenta)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-zero-or-more-times-lazy-match-).|*?|`\w*?d`corresponde a "modismo" e "ed" em "desbotado", mas não toda a palavra "desbotada" devido ao jogo preguiçoso|
|Encontrar a correspondência de uma ou mais ocorrências da expressão anterior (encontrar a correspondência do mínimo de caracteres possíveis). Para saber mais, confira [Corresponder a uma ou mais vezes (correspondência lenta)](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-one-or-more-times-lazy-match-).|+?|`e\w+?`corresponde "ee" em "adormecida" e "ed" em "desbotado", mas não encontra correspondências em "fade"|
|Ancorar a seqüência de correspondência para o [início de uma linha ou string](/dotnet/standard/base-types/anchors-in-regular-expressions#start-of-string-or-line-)|^|`^car`corresponde à palavra "carro" apenas quando ele aparece no início de uma linha|
|Ancorar a seqüência [de fósforos até](/dotnet/standard/base-types/anchors-in-regular-expressions#end-of-string-or-line-) o fim de uma linha|\r?$|`car\r?$`corresponde "carro" apenas quando ele aparece no final de uma linha|
|Ancorar a cadeia de caracteres de correspondência ao final do arquivo|$|`car$`corresponde "carro" apenas quando ele aparece no final do arquivo|
|Encontrar a correspondência de um único caractere em um conjunto|[abc]|`b[abc]`corresponde a "ba", "bb" e "bc"|
|Encontrar a correspondência de um caractere em um intervalo de caracteres|[a-f]|`be[n-t]`corresponde a "aposta" em "entre", "ben" em "abaixo" e "bes" em "ao lado", mas não encontra correspondências em "abaixo"|
|Capturar e numerar implicitamente a expressão contida entre parênteses|()|`([a-z])X\1` corresponde a “aXa” e “bXb”, mas não a “aXb”. “\1” se refere ao primeiro grupo de expressão “[a-z]”. Para saber mais, confira [Grupos de captura e padrões de substituição](#capture-groups-and-replacement-patterns). |
|Invalidar uma correspondência|(?!abc)|`real(?!ity)` corresponde a “real” em “realty” e “really”, mas não a “reality”. Também encontra o segundo “real” (mas não o primeiro “real”) em “realityreal”.|
|Encontrar a correspondência de um caractere que não está em um conjunto de caracteres específico. Para saber mais, veja [Negative Character Group (Grupo de caracteres negativos)](/dotnet/standard/base-types/character-classes-in-regular-expressions#negative-character-group-).|[^abc]|`be[^n-t]`corresponde "bef" em "antes", "beh" em "atrás" e "bel" em "abaixo", mas não encontra correspondências em "under"|
|Encontrar a correspondência da expressão antes ou depois do símbolo|&#124;|`(sponge|mud) bath`corresponde a "banho de esponja" e "banho de lama"|
|[Escape o personagem](/dotnet/standard/base-types/character-escapes-in-regular-expressions) seguindo a barra invertida| \\ |`\^`corresponde ao personagem ^|
|Especificar o número de ocorrências do caractere ou do grupo anterior. Para saber mais, confira [Corresponder a exatamente n vezes](/dotnet/standard/base-types/quantifiers-in-regular-expressions#match-exactly-n-times-n).|{n}, em que “n” é o número de ocorrências|`x(ab){2}x`corresponde a "xababx"<br/>`x(ab){2,3}x`corresponde "xababx" e "xabababx" mas não "xababababx"|
|[Corresponder ao texto em uma categoria Unicode](/dotnet/standard/base-types/character-classes-in-regular-expressions#unicode-category-or-unicode-block-p). Para saber mais sobre classes de caracteres Unicode, confira [Propriedades de caractere do Padrão Unicode 5.2](http://www.unicode.org/versions/Unicode5.2.0/ch04.pdf).|\p{X}, em que "X" é o número Unicode.|`\p{Lu}`corresponde a "T" e "D" em "Thomas Doe"|
|[Encontrar a correspondência de um limite de palavra](/dotnet/standard/base-types/anchors-in-regular-expressions#word-boundary-b)|\b (fora de uma classe de caractere, `\b` especifica um limite de palavra e, dentro de uma classe de caractere, `\b` especifica um backspace.)|`\bin`corresponde "in" em "inside" mas não encontra correspondências em "pinto"|
|Encontrar a correspondência de uma quebra de linha (isto é, um retorno de carro seguido por uma nova linha)|\r?\n|`End\r?\nBegin`corresponde "End" e "Begin" somente quando "End" é a última string em uma linha e "Begin" é a primeira string na próxima linha|
|Encontrar a correspondência de qualquer [caractere de palavra](/dotnet/standard/base-types/character-classes-in-regular-expressions#word-character-w)|\w|`a\wd`corresponde a "add" e "a1d" mas não "a d"|
|Combine qualquer [caractere de espaço branco](/dotnet/standard/base-types/character-classes-in-regular-expressions#whitespace-character-s)|\s|`Public\sInterface`corresponde à frase "Interface Pública"|
|Encontrar a correspondência de qualquer [caractere de dígito decimal](/dotnet/standard/base-types/character-classes-in-regular-expressions#decimal-digit-character-d)|\d|`\d`corresponde a "4" e "0" em "wd40"|

Um exemplo de expressão regular que combina alguns dos operadores e construções `\b0[xX]([0-9a-fA-F]+\)\b`para corresponder a um número hexadecimal é . Esta expressão corresponde a "0xc67f" mas não "0xc67g".

> [!TIP]
> Em sistemas operacionais Windows, a maioria das linhas termina em “\r\n” (um retorno de carro seguido por uma nova linha). Esses caracteres não são visíveis, mas estão presentes no editor e são passados para o serviço de expressão regular .NET.

## <a name="capture-groups-and-replacement-patterns"></a>Grupos de captura e padrões de substituição

Um grupo de captura delineia uma subexpressão de uma expressão regular e captura uma substring de uma cadeia de caracteres de entrada. Você pode usar os grupos capturados na expressão regular em si (por exemplo, para procurar uma palavra repetida) ou em um padrão de substituição. Para obter informações detalhadas, confira [Constructos de agrupamento em expressões regulares](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions).

Para criar um grupo de captura numerado, coloque a subexpressão entre parênteses no padrão de expressão regular. As capturas são numeradas automaticamente, da esquerda para a direita, com base na posição do parêntese de abertura na expressão regular. Para acessar o grupo capturado:

- **dentro da expressão** `\number`regular : Use . Por exemplo, `\1` na expressão regular `(\w+)\s\1` faz referência ao primeiro grupo de captura `(\w+)`.

- **em um padrão** `$number`de substituição : Use . Por exemplo, a expressão regular agrupada `(\d)([a-z])` define dois grupos: o primeiro grupo contém um único dígito decimal e o segundo grupo contém um único caractere entre **a** e **z**. A expressão localiza quatro correspondências na cadeia de caracteres a seguir: **1a 2b 3c 4d**. A cadeia de caracteres de substituição `z$1` faz referência somente ao primeiro grupo (`$1`) e converte a cadeia de caracteres em **z1 z2 z3 z4**.

A imagem a seguir mostra uma expressão regular `(\w+)\s\1` e uma cadeia de caracteres de substituição `$1`. A expressão regular e o padrão de substituição fazem referência ao primeiro grupo de captura que é automaticamente numerado como 1. Quando você escolhe **Substituir tudo** na caixa de diálogo **Substituição Rápida** no Visual Studio, palavras repetidas são removidas do texto.

![Substituição rápida mostrando um grupo de captura numerado no Visual Studio](media/numbered-capture-group.png)

> [!TIP]
> Verifique se o botão **Usar Expressões Regulares** está marcado na caixa de diálogo **Substituição Rápida**.

### <a name="named-capture-groups"></a>Grupos de captura nomeados

Em vez de depender da numeração automática de um grupo de captura, você pode dar a ele um nome. A sintaxe para um grupo de captura nomeado é `(?<name>subexpression)`.

Os grupos de captura nomeados, como grupos de captura numerados, podem ser usados na expressão regular em si ou em um padrão de substituição. Para acessar o grupo de captura nomeado:

- **dentro da expressão** `\k<name>`regular : Use . Por exemplo, `\k<repeated>` na expressão regular `(?<repeated>\w+)\s\k<repeated>` faz referência ao grupo de captura chamado `repeated` e cuja subexpressão é `\w+`.

- **em um padrão** `${name}`de substituição : Use . Por exemplo, `${repeated}`.

Como exemplo, a imagem a seguir mostra uma expressão regular `(?<repeated>\w+)\s\k<repeated>` e uma cadeia de caracteres de substituição `${repeated}`. A expressão regular e o padrão de substituição fazem referência ao primeiro grupo de captura nomeado `repeated`. Quando você escolhe **Substituir tudo** na caixa de diálogo **Substituição Rápida** no Visual Studio, palavras repetidas são removidas do texto.

![Substituição Rápida mostrando um grupo de captura nomeado no Visual Studio](media/named-capture-group.png)

> [!TIP]
> Verifique se o botão **Usar Expressões Regulares** está marcado na caixa de diálogo **Substituição Rápida**.

Para saber mais sobre grupos de captura nomeados, confira [Subexpressões coincidentes nomeadas](/dotnet/standard/base-types/grouping-constructs-in-regular-expressions#named-matched-subexpressions). Para saber mais sobre expressões regulares usadas em padrões de substituição, confira [Substituições em expressões regulares](/dotnet/standard/base-types/substitutions-in-regular-expressions).

## <a name="see-also"></a>Confira também

- [Linguagem de expressão regular](/dotnet/standard/base-types/regular-expression-language-quick-reference)
- [Encontrar e substituir texto](../ide/finding-and-replacing-text.md)
