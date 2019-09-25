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
ms.openlocfilehash: b197cacc764f1f5472d3eb074ac89199db508408
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233425"
---
# <a name="ca1820-test-for-empty-strings-using-string-length"></a>CA1820: Testar para verificar se há cadeias de caracteres vazias usando o tamanho da cadeia de caracteres

|||
|-|-|
|NomeDoTipo|TestForEmptyStringsUsingStringLength|
|CheckId|CA1820|
|Categoria|Microsoft.Performance|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Uma cadeia de caracteres é comparada com a <xref:System.Object.Equals%2A?displayProperty=nameWithType>cadeia de caracteres vazia usando.

## <a name="rule-description"></a>Descrição da regra

A comparação de cadeias de caracteres <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> usando a <xref:System.String.Length%2A?displayProperty=nameWithType> propriedade ou o <xref:System.Object.Equals%2A>método é mais rápida do que usar. Isso ocorre porque <xref:System.Object.Equals%2A> o executa significativamente mais instruções MSIL do que <xref:System.String.IsNullOrEmpty%2A> um ou o número de instruções executadas para recuperar <xref:System.String.Length%2A> o valor da propriedade e compará-lo com zero.

Para cadeias de <xref:System.Object.Equals%2A> caracteres `<string>.Length == 0` nulas e se comportam de forma diferente. Se você tentar obter o valor da <xref:System.String.Length%2A> Propriedade em uma cadeia de caracteres nula, a Common Language Runtime lançará um. <xref:System.NullReferenceException?displayProperty=fullName> Se você executar uma comparação entre uma cadeia de caracteres nula e uma cadeia de caracteres vazia, a Common Language Runtime não lançará `false`uma exceção e retornará. O teste de NULL não afeta significativamente o desempenho relativo dessas duas abordagens. Ao direcionar .NET Framework 2,0 ou posterior, use <xref:System.String.IsNullOrEmpty%2A> o método. Caso contrário, use <xref:System.String.Length%2A> a comparação = = 0 sempre que possível.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere a comparação para usar o <xref:System.String.IsNullOrEmpty%2A> método.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra se o desempenho não for um problema.

## <a name="example"></a>Exemplo

O exemplo a seguir ilustra as diferentes técnicas que são usadas para procurar uma cadeia de caracteres vazia.

[!code-csharp[FxCop.Performance.StringTest#1](../code-quality/codesnippet/CSharp/ca1820-test-for-empty-strings-using-string-length_1.cs)]