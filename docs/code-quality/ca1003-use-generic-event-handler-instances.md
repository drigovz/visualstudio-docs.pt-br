---
title: 'CA1003: usar instâncias do manipulador de eventos genéricos'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 42e40acfc8034f27c8b9131b6d5c8f8bb2f95dcb
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72441726"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: usar instâncias do manipulador de eventos genéricos

|||
|-|-|
|NomeDoTipo|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Categoria|Microsoft. Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo contém um delegado que retorna void e cuja assinatura contém dois parâmetros (o primeiro objeto e o segundo tipo que pode ser atribuído a EventArgs) e o assembly que o contém tem como destino .NET.

Por padrão, essa regra só examina os tipos visíveis externamente, mas isso é [configurável](#configurability).

## <a name="rule-description"></a>Descrição da regra

Antes do .NET, para passar informações personalizadas para o manipulador de eventos, um novo delegado tinha de ser declarado que especificou uma classe que era derivada da classe <xref:System.EventArgs?displayProperty=fullName>. No .NET, o delegado <xref:System.EventHandler%601?displayProperty=fullName> genérico permite que qualquer classe derivada de <xref:System.EventArgs> seja usada junto com o manipulador de eventos.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, remova o delegado e substitua seu uso usando o delegado <xref:System.EventHandler%601?displayProperty=fullName>.

Se o delegado for gerado automaticamente pelo compilador Visual Basic, altere a sintaxe da declaração de evento para usar o delegado <xref:System.EventHandler%601?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="configurability"></a>Configurabilidade

Se você estiver executando essa regra por meio de [analisadores do FxCop](install-fxcop-analyzers.md) (e não com a análise herdada), poderá configurar em quais partes de sua base de código executar essa regra, com base em sua acessibilidade. Por exemplo, para especificar que a regra deve ser executada somente na superfície da API não pública, adicione o seguinte par chave-valor a um arquivo. editorconfig em seu projeto:

```ini
dotnet_code_quality.ca1003.api_surface = private, internal
```

Você pode configurar essa opção apenas para essa regra, para todas as regras ou para todas as regras nesta categoria (Design). Para obter mais informações, consulte [Configurar analisadores de FxCop](configure-fxcop-analyzers.md).

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um delegado que viola a regra. No exemplo a Visual Basic, os comentários descrevem como modificar o exemplo para atender à regra. Para o C# exemplo, um exemplo a seguir mostra o código modificado.

[!code-vb[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/VisualBasic/ca1003-use-generic-event-handler-instances_1.vb)]
[!code-csharp[FxCop.Design.CustomEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_1.cs)]

O trecho de código a seguir remove a declaração delegate do exemplo anterior, que satisfaz a regra. Ele substitui seu uso nos métodos `ClassThatRaisesEvent` e `ClassThatHandlesEvent` usando o delegado <xref:System.EventHandler%601?displayProperty=fullName>.

[!code-csharp[FxCop.Design.GenericEventHandler#1](../code-quality/codesnippet/CSharp/ca1003-use-generic-event-handler-instances_2.cs)]

## <a name="related-rules"></a>Regras relacionadas

- [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)
- [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)
- [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)
- [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)
- [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)
- [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)
- [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também

- [Genéricos](/dotnet/csharp/programming-guide/generics/index)
