---
title: 'CA1005: Evitar parâmetros excessivos em tipos genéricos'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
helpviewer_keywords:
- AvoidExcessiveParametersOnGenericTypes
- CA1005
ms.assetid: 372b2f28-5c59-4815-9753-6c65b2bb3589
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ffc94a04d708315cc143afd1556cb8a2f0072e91
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68923295"
---
# <a name="ca1005-avoid-excessive-parameters-on-generic-types"></a>CA1005: Evitar parâmetros excessivos em tipos genéricos

|||
|-|-|
|NomeDoTipo|AvoidExcessiveParametersOnGenericTypes|
|CheckId|CA1005|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo genérico visível externamente tem mais de dois parâmetros de tipo.

## <a name="rule-description"></a>Descrição da regra
Quanto mais parâmetros de tipo um tipo genérico contiver, mais difícil será saber e lembrar-se do que cada parâmetro de tipo representa. Normalmente, isso é óbvio com um parâmetro de tipo, `List<T>`como em, e em determinados casos com dois parâmetros de tipo `Dictionary<TKey, TValue>`, como em. Se houver mais de dois parâmetros de tipo, a dificuldade se tornará muito grande para a maioria dos `TooManyTypeParameters<T, K, V>` usuários ( `TooManyTypeParameters(Of T, K, V)` por [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]exemplo, no C# ou no).

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, altere o design para não usar mais do que dois parâmetros de tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir um aviso dessa regra, a menos que o design absolutamente exija mais do que dois parâmetros de tipo. Fornecer genéricos em uma sintaxe que seja fácil de entender e usar reduz o tempo necessário para aprender e aumentar a taxa de adoção de novas bibliotecas.

## <a name="related-rules"></a>Regras relacionadas
[CA1010: As coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

[CA1000: Não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

[CA1002: Não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

[CA1006: Não aninhe tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

[CA1004: Métodos genéricos devem fornecer parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

[CA1003: Usar instâncias de manipulador de eventos genéricas](../code-quality/ca1003-use-generic-event-handler-instances.md)

[CA1007: Usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
[Genéricos](/dotnet/csharp/programming-guide/generics/index)