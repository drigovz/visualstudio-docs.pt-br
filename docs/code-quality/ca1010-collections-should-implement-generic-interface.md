---
title: 'CA1010: as coleções devem implementar a interface genérica'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
helpviewer_keywords:
- CA1010
- CollectionsShouldImplementGenericInterface
ms.assetid: c7d7126f-fa70-40be-8f93-3243e1760dc5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d3e50fb93e8cdfe6f65fe1b2de1da54b58a6a8c9
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72449316"
---
# <a name="ca1010-collections-should-implement-generic-interface"></a>CA1010: as coleções devem implementar a interface genérica

|||
|-|-|
|NomeDoTipo|CollectionsShouldImplementGenericInterface|
|CheckId|CA1010|
|Categoria|Microsoft. Design|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo implementa a interface <xref:System.Collections.IEnumerable?displayProperty=fullName>, mas não implementa a interface <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName> e o assembly que o contém tem como destino .NET. Essa regra ignora os tipos que implementam <xref:System.Collections.IDictionary?displayProperty=fullName>.

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Para ampliar a usabilidade de uma coleção, implemente uma das interfaces da coleção genéricas. Em seguida, a coleção pode ser usada para preencher tipos de coleção genéricos, como o seguinte:

- <xref:System.Collections.Generic.List%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Queue%601?displayProperty=fullName>
- <xref:System.Collections.Generic.Stack%601?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, implemente uma das seguintes interfaces de coleção genéricas:

- <xref:System.Collections.Generic.IEnumerable%601?displayProperty=fullName>
- <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>
- <xref:System.Collections.Generic.IList%601?displayProperty=fullName>

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra; no entanto, o uso da coleção será mais limitado.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1010.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example-violation"></a>Violação de exemplo

O exemplo a seguir mostra uma classe (tipo de referência) que deriva da classe não genérica `CollectionBase`, que viola essa regra.

[!code-csharp[FxCop.Design.CollectionsGenericViolation#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_1.cs)]

Para corrigir uma violação dessa regra, siga um destes procedimentos:

- Implemente as interfaces genéricas.
- Altere a classe base para um tipo que já implemente as interfaces genéricas e não genéricas, como a classe `Collection<T>`.

## <a name="fix-by-base-class-change"></a>Correção por alteração de classe base

O exemplo a seguir corrige a violação alterando a classe base da coleção da classe não genérica `CollectionBase` para a classe genérica `Collection<T>` (`Collection(Of T)` em Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericBase#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_2.cs)]

A alteração da classe base de uma classe já lançada é considerada uma alteração significativa nos consumidores existentes.

## <a name="fix-by-interface-implementation"></a>Corrigir por implementação de interface

O exemplo a seguir corrige a violação implementando essas interfaces genéricas: `IEnumerable<T>`, `ICollection<T>` e `IList<T>` (`IEnumerable(Of T)`, `ICollection(Of T)` e `IList(Of T)` em Visual Basic).

[!code-csharp[FxCop.Design.CollectionsGenericInterface#1](../code-quality/codesnippet/CSharp/ca1010-collections-should-implement-generic-interface_3.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1003: usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)
- [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)
