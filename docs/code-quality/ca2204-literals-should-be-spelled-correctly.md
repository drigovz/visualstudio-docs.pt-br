---
title: 'CA2204: Literais devem ser escritos corretamente'
ms.date: 03/28/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62ad30516720a843d519a9e514cd325a957b3cff
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017117"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Literais devem ser escritos corretamente

|||
|-|-|
|NomeDoTipo|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Uma cadeia de caracteres literal é passada como um argumento para um parâmetro localizável, ou a uma propriedade localizável, e a cadeia de caracteres contém uma ou mais palavras não reconhecidas pela biblioteca do verificador ortográfico da Microsoft.

## <a name="rule-description"></a>Descrição da regra

Esta regra verifica uma cadeia de caracteres literal que é passada como um valor para um parâmetro ou uma propriedade quando um ou mais dos seguintes casos é verdadeiro:

- O <xref:System.ComponentModel.LocalizableAttribute> atributo do parâmetro ou da propriedade é definido como true.

- O nome de parâmetro ou a propriedade contém "Text", "Mensagem" ou "Legenda".

- O nome da variável de cadeia de caracteres que é passado para um <xref:System.Console.Write%2A> ou <xref:System.Console.WriteLine> método é "valor" ou "formato".

Esta regra analisa a cadeia de caracteres literal em palavras, criar tokens de palavras compostas e verifica a ortografia de cada palavra ou um token. Para obter informações sobre o algoritmo de análise, consulte [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

## <a name="language"></a>Idioma

O verificador ortográfico verifica atualmente apenas em relação a dicionários de cultura baseada em inglês. Você pode alterar a cultura do seu projeto no arquivo de projeto, adicionando a **CodeAnalysisCulture** elemento.

Por exemplo:

```xml
<Project ...>
  <PropertyGroup>
    <CodeAnalysisCulture>en-AU</CodeAnalysisCulture>
```

> [!IMPORTANT]
> Se você definir a cultura como algo diferente de uma cultura com base em inglês, essa regra de análise de código é silenciosamente desabilitada.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, corrija a grafia da palavra ou adicionar a palavra a um dicionário personalizado. Para obter informações sobre como usar dicionários personalizados, consulte [como: Personalizar o dicionário de análise de código](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Corretamente as palavras escritas de reduzem a curva de aprendizado necessária para novas bibliotecas de software.

## <a name="related-rules"></a>Regras relacionadas

- [CA1704: Identificadores devem ter grafia correta](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)
- [CA1703: Cadeias de caracteres de recurso devem ter grafia correta](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)