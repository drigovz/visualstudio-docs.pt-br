---
title: 'CA1820: Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
helpviewer_keywords:
- TestForEmptyStringsUsingStringLength
- CA1820
ms.assetid: da1e70c8-b1dc-46b9-8b8f-4e6e48339681
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb5160ef663375ee3dd4b45797e8f4536acdf793
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66744653"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres

|||
|-|-|
|NomeDoTipo|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Categoria|Microsoft.Performance|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Uma cadeia de caracteres é comparado com a cadeia de caracteres vazia usando <xref:System.Object.Equals%2A?displayProperty=nameWithType>.

## <a name="rule-description"></a>Descrição da regra

Comparando cadeias de caracteres usando o <xref:System.String.Length%2A?displayProperty=nameWithType> propriedade ou o <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> método é mais rápido que usar <xref:System.Object.Equals%2A>. Isso ocorre porque <xref:System.Object.Equals%2A> executa significativamente mais instruções MSIL que ambos <xref:System.String.IsNullOrEmpty%2A> ou o número de instruções executadas para recuperar o <xref:System.String.Length%2A> propriedade de valor e compará-la como zero.

Para cadeias de caracteres nulas <xref:System.Object.Equals%2A> e `<string>.Length == 0` se comportam de maneira diferente. Se você tentar obter o valor de <xref:System.String.Length%2A> propriedade em uma cadeia de caracteres nula, o common language runtime lançará uma <xref:System.NullReferenceException?displayProperty=fullName>. Se você realizar uma comparação entre uma cadeia de caracteres nula e a cadeia de caracteres vazia, o common language runtime não lança uma exceção e retorna `false`. Testando null não afeta significativamente o desempenho relativo dessas duas abordagens. Quando direcionados ao .NET Framework 2.0 ou posterior, use o <xref:System.String.IsNullOrEmpty%2A> método. Caso contrário, use o <xref:System.String.Length%2A> = = 0 comparação sempre que possível.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere a comparação para usar o <xref:System.String.IsNullOrEmpty%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso nessa regra, se o desempenho não for um problema.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra as técnicas diferentes que são usadas para procurar uma cadeia de caracteres vazia.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]