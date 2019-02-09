---
title: 'CA2217: Não marcar enumerações com FlagsAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
helpviewer_keywords:
- DoNotMarkEnumsWithFlags
- CA2217
dev_langs:
- VB
- CSharp
- CPP
ms.assetid: 1b6f626c-66bf-45b0-a3e2-7c41ee9ceda7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce4036ef3c0c9ea177ea4225ed10ca7cfe128697
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55926808"
---
# <a name="ca2217-do-not-mark-enums-with-flagsattribute"></a>CA2217: Não marcar enumerações com FlagsAttribute

|||
|-|-|
|NomeDoTipo|DoNotMarkEnumsWithFlags|
|CheckId|CA2217|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa

Uma enumeração visível externamente é marcada com <xref:System.FlagsAttribute>e ele tem um ou mais valores que não são potências de dois ou uma combinação dos outros os valores definidos na enumeração.

## <a name="rule-description"></a>Descrição da regra

Uma enumeração deve ter <xref:System.FlagsAttribute> presente somente se cada valor definido na enumeração é uma potência de dois ou uma combinação de valores de definidos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova <xref:System.FlagsAttribute> da enumeração.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example-that-should-not-have-the-attribute"></a>Exemplo que não deve ter o atributo

O exemplo a seguir mostra uma enumeração, `Color`, que contém o valor 3. 3 não é uma potência de dois, ou uma combinação de qualquer um dos valores definidos. O `Color` enumeração não deve ser marcada com <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_1.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_1.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_1.vb)]

## <a name="example-that-should-have-the-attribute"></a>Exemplo que deve ter o atributo

O exemplo a seguir mostra uma enumeração `Days`, que atende aos requisitos do que está sendo marcado com <xref:System.FlagsAttribute>.

[!code-cpp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CPP/ca2217-do-not-mark-enums-with-flagsattribute_2.cpp)]
[!code-csharp[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/CSharp/ca2217-do-not-mark-enums-with-flagsattribute_2.cs)]
[!code-vb[FxCop.Usage.EnumNoFlags2#1](../code-quality/codesnippet/VisualBasic/ca2217-do-not-mark-enums-with-flagsattribute_2.vb)]

## <a name="related-rules"></a>Regras relacionadas

[CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também

- <xref:System.FlagsAttribute?displayProperty=fullName>
