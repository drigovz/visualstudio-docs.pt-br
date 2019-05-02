---
title: 'CA1000: Não declarar membros estáticos em tipos genéricos'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1000
- DoNotDeclareStaticMembersOnGenericTypes
helpviewer_keywords:
- DoNotDeclareStaticMembersOnGenericTypes
- CA1000
ms.assetid: 5c0da594-f8d0-4f40-953d-56bf7fbd2087
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: a4e963df54d9cdf6433ef34808d64fe81c9297d9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62779916"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Não declarar membros estáticos em tipos genéricos

|||
|-|-|
|NomeDoTipo|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo genérico contiver uma `static` (`Shared` no Visual Basic) membros.

Por padrão, essa regra olha apenas tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Quando um `static` membro de um tipo genérico é chamado, o argumento de tipo deve ser especificado para o tipo. Quando um membro de instância genérico que não dá suporte à inferência é chamado, o argumento de tipo deve ser especificado para o membro. A sintaxe para especificar o argumento de tipo nesses dois casos é diferente e facilmente confundida, como demonstram as seguintes chamadas:

```vb
' Shared method in a generic type.
GenericType(Of Integer).SharedMethod()

' Generic instance method that does not support inference.
someObject.GenericMethod(Of Integer)()
```

```csharp
// Static method in a generic type.
GenericType<int>.StaticMethod();

// Generic instance method that does not support inference.
someObject.GenericMethod<int>();
```

Em geral, ambas as declarações anteriores devem ser evitadas para que o argumento de tipo não precisa ser especificado quando o membro é chamado. Isso resulta em uma sintaxe de chamada membros genéricos não é diferente da sintaxe de não-genéricos. Para obter mais informações, consulte [CA1004: Métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md).

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o membro estático ou alterá-lo para um membro de instância.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Fornecer genéricos em uma sintaxe fácil de entender e usar reduz o tempo que é necessário para saber mais e aumenta a taxa de adoção de novas bibliotecas.

## <a name="configurability"></a>Capacidade de configuração

Se você estiver executando essa regra de [analisadores FxCop](install-fxcop-analyzers.md) (e não por meio de análise de código estático), você pode configurar quais partes da sua base de código para executar essa regra, com base na sua acessibilidade. Por exemplo, para especificar que a regra deve ser executado apenas em relação a superfície de API não público, adicione o seguinte par de chave-valor para um arquivo. editorconfig em seu projeto:

```
dotnet_code_quality.ca1000.api_surface = private, internal
```

Você pode configurar essa opção para apenas essa regra, para todas as regras ou para todas as regras nessa categoria (Design). Para obter mais informações, consulte [analisadores FxCop configurar](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1005: Evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: As coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002: Não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)