---
title: 'CA1006: Não aninhar tipos genéricos em assinaturas de membro'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotNestGenericTypesInMemberSignatures
- CA1006
helpviewer_keywords:
- CA1006
- DoNotNestGenericTypesInMemberSignatures
ms.assetid: dfc867bc-f4af-45d7-b071-db04a248f9fc
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 45ff4831875150df02d04553e75cebcab9a9f572
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236500"
---
# <a name="ca1006-do-not-nest-generic-types-in-member-signatures"></a>CA1006: Não aninhar tipos genéricos em assinaturas de membro

|||
|-|-|
|NomeDoTipo|DoNotNestGenericTypesInMemberSignatures|
|CheckId|CA1006|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um membro visível externamente tem uma assinatura que contém um argumento de tipo aninhado.

## <a name="rule-description"></a>Descrição da regra
Um argumento de tipo aninhado é um argumento de tipo que também é um tipo genérico. Para chamar um membro cuja assinatura contenha um argumento de tipo aninhado, o usuário deve criar uma instância de um tipo genérico e passar esse tipo para o construtor de um segundo tipo genérico. O procedimento e a sintaxe obrigatórios são complexos e devem ser evitados.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o design para remover o argumento de tipo aninhado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra. Fornecer genéricos em uma sintaxe que seja fácil de entender e usar reduz o tempo necessário para aprender e aumentar a taxa de adoção de novas bibliotecas.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um método que viola a regra e a sintaxe necessária para chamar o método de violação.

[!code-vb[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/VisualBasic/ca1006-do-not-nest-generic-types-in-member-signatures_1.vb)]
[!code-csharp[FxCop.Design.NestedGenerics#1](../code-quality/codesnippet/CSharp/ca1006-do-not-nest-generic-types-in-member-signatures_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1005: Evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

[CA1010: As coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1004: Métodos genéricos devem fornecer parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usar instâncias de manipulador de eventos genéricas](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
[Genéricos](/dotnet/csharp/programming-guide/generics/index)