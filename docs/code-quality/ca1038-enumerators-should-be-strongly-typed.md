---
title: 'CA1038: os enumeradores devem ser fortemente tipados'
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
ms.openlocfilehash: 22d3ebbbce2a2495e32e55dca85f9db35b09a06d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449246"
---
# <a name="ca1038-enumerators-should-be-strongly-typed"></a>CA1038: os enumeradores devem ser fortemente tipados

|||
|-|-|
|NomeDoTipo|EnumeratorsShouldBeStronglyTyped|
|CheckId|CA1038|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo público ou protegido implementa <xref:System.Collections.IEnumerator?displayProperty=fullName>, mas não fornece uma versão fortemente tipada da propriedade <xref:System.Collections.IEnumerator.Current%2A?displayProperty=fullName>. Tipos que são derivados dos seguintes tipos são isentos desta regra:

- <xref:System.Collections.CollectionBase?displayProperty=fullName>

- <xref:System.Collections.DictionaryBase?displayProperty=fullName>

- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

## <a name="rule-description"></a>Descrição da regra
Essa regra requer implementações <xref:System.Collections.IEnumerator> para também fornecer uma versão fortemente tipada da propriedade <xref:System.Collections.IEnumerator.Current%2A> para que os usuários não precisem converter o valor de retorno para o tipo forte ao usarem a funcionalidade fornecida pela interface. Essa regra pressupõe que o tipo que implementa <xref:System.Collections.IEnumerator> contém uma coleção de instâncias de um tipo que é mais forte que <xref:System.Object>.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente a propriedade de interface explicitamente (declare-a como `IEnumerator.Current`). Adicione uma versão pública com rigidez de tipos da propriedade, declarada como `Current`, e faça com que ela retorne um objeto fortemente tipado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso desta regra ao implementar um enumerador baseado em objeto para uso com uma coleção baseada em objeto, como uma árvore binária. Os tipos que estendem a nova coleção definirão o enumerador fortemente tipado e exporão a propriedade fortemente tipada.

## <a name="example"></a>Exemplo
O exemplo a seguir demonstra a maneira correta de implementar um tipo <xref:System.Collections.IEnumerator> fortemente tipado.

[!code-csharp[FxCop.Design.IEnumeratorStrongTypes#1](../code-quality/codesnippet/CSharp/ca1038-enumerators-should-be-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1035: as implementações de ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1039: as listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.IEnumerator?displayProperty=fullName>
- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.DictionaryBase?displayProperty=fullName>
- <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>
