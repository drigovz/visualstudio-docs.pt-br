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
ms.openlocfilehash: 4cc33c51af7d596fb9c784b76f8cc2f255ddf5a5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236711"
---
# <a name="ca1000-do-not-declare-static-members-on-generic-types"></a>CA1000: Não declarar membros estáticos em tipos genéricos

|||
|-|-|
|NomeDoTipo|DoNotDeclareStaticMembersOnGenericTypes|
|CheckId|CA1000|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo genérico contém um `static` membro`Shared` (no Visual Basic).

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Quando um `static` membro de um tipo genérico é chamado, o argumento de tipo deve ser especificado para o tipo. Quando um membro de instância genérico que não dá suporte à inferência é chamado, o argumento de tipo deve ser especificado para o membro. A sintaxe para especificar o argumento de tipo nesses dois casos é diferente e facilmente confundida, uma vez que as seguintes chamadas demonstram:

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

Em geral, ambas as declarações anteriores devem ser evitadas para que o argumento de tipo não precise ser especificado quando o membro for chamado. Isso resulta em uma sintaxe para chamar Membros em genéricos que não é diferente da sintaxe para não genéricos. Para obter mais informações, [consulte CA1004: Os métodos genéricos devem fornecer o](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)parâmetro de tipo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o membro estático ou altere-o para um membro da instância.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra. Fornecer genéricos em uma sintaxe que seja fácil de entender e usar reduz o tempo necessário para aprender e aumentar a taxa de adoção de novas bibliotecas.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1000.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regras relacionadas

- [CA1005: Evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: As coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1002: Não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: Não aninhe tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: Métodos genéricos devem fornecer parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: Usar instâncias de manipulador de eventos genéricas](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: Usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)