---
title: 'CA1035: Implementações ICollection têm membros fortemente tipados'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ICollectionImplementationsHaveStronglyTypedMembers
- CA1035
helpviewer_keywords:
- CA1035
- ICollectionImplementationsHaveStronglyTypedMembers
ms.assetid: ad404eb5-cf6a-44b7-b78a-8ebfb654bc7f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a20feb514b87f2906fd4db32dfb38d3d9b661999
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922828"
---
# <a name="ca1035-icollection-implementations-have-strongly-typed-members"></a>CA1035: Implementações ICollection têm membros fortemente tipados

|||
|-|-|
|NomeDoTipo|ICollectionImplementationsHaveStronglyTypedMembers|
|CheckId|CA1035|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo público ou protegido implementa <xref:System.Collections.ICollection?displayProperty=fullName> , mas não fornece um método fortemente tipado <xref:System.Collections.ICollection.CopyTo%2A?displayProperty=fullName>para. A versão fortemente tipada <xref:System.Collections.ICollection.CopyTo%2A> do deve aceitar dois parâmetros e não pode <xref:System.Array?displayProperty=fullName> ter um ou uma <xref:System.Object?displayProperty=fullName> matriz de como seu primeiro parâmetro.

## <a name="rule-description"></a>Descrição da regra
Essa regra requer <xref:System.Collections.ICollection> implementações para fornecer membros fortemente tipados para que os usuários não precisem converter argumentos <xref:System.Object> para o tipo quando usarem a funcionalidade fornecida pela interface. Essa regra pressupõe que o tipo que implementa <xref:System.Collections.ICollection> faz isso para gerenciar uma coleção de instâncias de um tipo que é mais forte <xref:System.Object>do que.

 <xref:System.Collections.ICollection> implementa a interface <xref:System.Collections.IEnumerable?displayProperty=fullName>. Se os objetos na coleção se estenderem <xref:System.ValueType?displayProperty=fullName>, você deverá fornecer um membro fortemente tipado para <xref:System.Collections.IEnumerable.GetEnumerator%2A> para evitar a redução no desempenho causado por boxing. Isso não é necessário quando os objetos da coleção são um tipo de referência.

Para implementar uma versão fortemente tipada de um membro de interface, implemente os membros da interface explicitamente usando nomes `InterfaceName.InterfaceMemberName`no formulário, <xref:System.Collections.ICollection.CopyTo%2A>como. Os membros da interface explícita usam os tipos de dados declarados pela interface. Implemente os membros fortemente tipados usando o nome de membro da interface <xref:System.Collections.ICollection.CopyTo%2A>, como. Declare os membros fortemente tipados como públicos e declare parâmetros e valores de retorno como sendo do tipo forte que é gerenciado pela coleção. Os tipos fortes substituem tipos mais <xref:System.Object> fracos, como e <xref:System.Array> que são declarados pela interface.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, implemente o membro da interface explicitamente (declare- <xref:System.Collections.ICollection.CopyTo%2A>o como). Adicione o membro fortemente tipado público, declarado `CopyTo`como, e faça com que ele use uma matriz fortemente tipada como seu primeiro parâmetro.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Suprimir um aviso dessa regra se você implementar uma nova coleção baseada em objeto, como uma árvore binária, em que os tipos que estendem a nova coleção determinam o tipo forte. Esses tipos devem estar em conformidade com essa regra e expor membros fortemente tipados.

## <a name="example"></a>Exemplo
O exemplo a seguir demonstra a maneira correta de <xref:System.Collections.ICollection>implementar.

[!code-csharp[FxCop.Design.ICollectionStrongTypes#1](../code-quality/codesnippet/CSharp/ca1035-icollection-implementations-have-strongly-typed-members_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1038: Enumeradores devem ser fortemente tipados](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)

[CA1039: As listas são fortemente tipadas](../code-quality/ca1039-lists-are-strongly-typed.md)

## <a name="see-also"></a>Consulte também

- <xref:System.Array?displayProperty=fullName>
- <xref:System.Collections.IEnumerable?displayProperty=fullName>
- <xref:System.Collections.ICollection?displayProperty=fullName>
- <xref:System.Object?displayProperty=fullName>