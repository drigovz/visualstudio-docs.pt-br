---
title: 'CA1813: Evitar atributos não selados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1813
- AvoidUnsealedAttributes
helpviewer_keywords:
- CA1813
- AvoidUnsealedAttributes
ms.assetid: f5e31b4c-9f8b-49e1-a2a8-bb5f1140729a
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 12371c34c846991a0ec41f5e9d9588c5bde8e4d6
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233592"
---
# <a name="ca1813-avoid-unsealed-attributes"></a>CA1813: Evitar atributos não selados

|||
|-|-|
|NomeDoTipo|AvoidUnsealedAttributes|
|CheckId|CA1813|
|Categoria|Microsoft.Performance|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo público herda de <xref:System.Attribute?displayProperty=fullName>, não é abstrato e não é lacrado (`NotInheritable` em Visual Basic).

## <a name="rule-description"></a>Descrição da regra

O .NET fornece métodos para recuperar atributos personalizados. Por padrão, esses métodos pesquisam a hierarquia de herança do atributo. Por exemplo, <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=fullName> pesquisa o tipo de atributo especificado ou qualquer tipo de atributo que estenda o tipo de atributo especificado. Lacrar o atributo elimina a pesquisa por meio da hierarquia de herança e pode melhorar o desempenho.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, lacre o tipo de atributo ou torne-o abstrato.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra. Suprime somente se você estiver definindo uma hierarquia de atributo e não puder lacrar o atributo ou torná-lo abstrato.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um atributo personalizado que satisfaz essa regra.

[!code-csharp[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/CSharp/ca1813-avoid-unsealed-attributes_1.cs)]
[!code-vb[FxCop.Performance.AttributesSealed#1](../code-quality/codesnippet/VisualBasic/ca1813-avoid-unsealed-attributes_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1019: Definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)
- [CA1018: Marcar atributos com AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)

## <a name="see-also"></a>Consulte também

- [Atributos](/dotnet/standard/design-guidelines/attributes)