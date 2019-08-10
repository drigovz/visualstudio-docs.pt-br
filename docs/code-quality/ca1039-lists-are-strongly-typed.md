---
title: 'CA1039: Listas são fortemente tipadas'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1039
- ListsAreStronglyTyped
helpviewer_keywords:
- CA1039
- ListsAreStronglyTyped
ms.assetid: 5ac366c4-fd87-4d5c-95d5-f755510c8e5c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 94b1e8134eb89e4ae78ec0ad6f07fd7406215185
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922840"
---
# <a name="ca1039-lists-are-strongly-typed"></a>CA1039: Listas são fortemente tipadas

|||
|-|-|
|NomeDoTipo|ListsAreStronglyTyped|
|CheckId|CA1039|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

O tipo público ou protegido implementa <xref:System.Collections.IList?displayProperty=fullName> , mas não fornece um método fortemente tipado para um ou mais dos seguintes:

- IList.Item

- IList. Add

- IList. Contains

- IList. IndexOf

- IList. Insert

- IList.Remove

## <a name="rule-description"></a>Descrição da regra

Essa regra requer <xref:System.Collections.IList> implementações para fornecer membros fortemente tipados, de modo que os usuários não precisem converter <xref:System.Object?displayProperty=fullName> argumentos para o tipo quando usam a funcionalidade fornecida pela interface. A <xref:System.Collections.IList> interface é implementada por coleções de objetos que podem ser acessados por índice. Essa regra pressupõe que o tipo que implementa <xref:System.Collections.IList> gerencia uma coleção de instâncias de um tipo que é mais forte <xref:System.Object>do que.

<xref:System.Collections.IList>implementa as <xref:System.Collections.ICollection?displayProperty=fullName> interfaces <xref:System.Collections.IEnumerable?displayProperty=fullName> e. Se você implementar <xref:System.Collections.IList>o, deverá fornecer os membros com rigidez de tipos <xref:System.Collections.ICollection>necessários para o. Se os objetos na coleção se estenderem <xref:System.ValueType?displayProperty=fullName>, você deverá fornecer um membro fortemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar a redução no desempenho causado por Boxing; isso não é necessário quando os objetos da coleção são um tipo de referência.

Para obedecer a essa regra, implemente os membros da interface explicitamente usando nomes no formato InterfaceName. InterfaceMemberName, como <xref:System.Collections.IList.Add%2A>. Os membros da interface explícita usam os tipos de dados declarados pela interface. Implemente os membros fortemente tipados usando o nome de membro da interface `Add`, como. Declare os membros fortemente tipados como públicos e declare parâmetros e valores de retorno como sendo do tipo forte que é gerenciado pela coleção. Os tipos fortes substituem tipos mais <xref:System.Object> fracos, como e <xref:System.Array> que são declarados pela interface.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente <xref:System.Collections.IList> explicitamente os membros e forneça alternativas fortemente tipadas para os membros que foram observados anteriormente. Para o código que implementa corretamente <xref:System.Collections.IList> a interface e fornece os membros com rigidez de tipos necessários, consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso desta regra ao implementar uma nova coleção baseada em objeto, como uma lista vinculada, em que os tipos que estendem a nova coleção determinam o tipo forte. Esses tipos devem estar em conformidade com essa regra e expor membros fortemente tipados.

## <a name="example"></a>Exemplo
No exemplo a seguir, o tipo `YourType` se <xref:System.Collections.CollectionBase?displayProperty=fullName>estende, pois todas as coleções com rigidez de tipos devem ser. <xref:System.Collections.CollectionBase>fornece a implementação explícita da <xref:System.Collections.IList> interface para você. Portanto, você deve fornecer somente os membros fortemente tipados <xref:System.Collections.IList> para <xref:System.Collections.ICollection>e.

[!code-csharp[FxCop.Design.IListStrongTypes#1](../code-quality/codesnippet/CSharp/ca1039-lists-are-strongly-typed_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1035: Implementações ICollection têm membros fortemente tipados](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)

[CA1038: Enumeradores devem ser fortemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.CollectionBase?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.IList?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>