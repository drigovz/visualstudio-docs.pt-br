---
title: 'CA1038: Enumeradores devem ser fortemente tipados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
helpviewer_keywords:
- EnumeratorsShouldBeStronglyTyped
- CA1038
ms.assetid: 8919f526-d487-42a4-87dc-2b2ee25260c4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 56c2281f76b9064427d1d651523b9cda441eb029
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236010"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: Enumeradores devem ser fortemente tipados

|||
|-|-|
|NomeDoTipo|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo público ou protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName> , mas não fornece uma versão fortemente tipada <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName> da propriedade. Tipos que são derivados dos seguintes tipos são isentos desta regra:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descrição da regra
Essa regra requer <xref:System.Collections.IEnumerator> implementações para também fornecer uma versão fortemente tipada <xref:System.Collections.IEnumerator.Current%2A> da propriedade para que os usuários não precisem converter o valor de retorno para o tipo forte ao usarem a funcionalidade fornecida pela interface. Essa regra pressupõe que o tipo que implementa <xref:System.Collections.IEnumerator> contém uma coleção de instâncias de um tipo que é mais forte <xref:System.Object>que.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente a propriedade de interface explicitamente (declare- `IEnumerator.Current`a como). Adicione uma versão pública com rigidez de tipos da propriedade, declarada como `Current`e faça com que ela retorne um objeto fortemente tipado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso desta regra ao implementar um enumerador baseado em objeto para uso com uma coleção baseada em objeto, como uma árvore binária. Os tipos que estendem a nova coleção definirão o enumerador fortemente tipado e exporão a propriedade fortemente tipada.

## <a name="example"></a>Exemplo
O exemplo a seguir demonstra a maneira correta de implementar um tipo <xref:System.Collections.IEnumerator> fortemente tipado.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1035: Implementações ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: As listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>