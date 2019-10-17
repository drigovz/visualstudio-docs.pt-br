---
title: 'CA1402: evitar sobrecargas em interfaces visíveis COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1617ad2d5132f22da3c25565e6310977b286eaef
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444332"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: evitar sobrecargas em interfaces visíveis COM

|||
|-|-|
|NomeDoTipo|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Uma interface visível de Component Object Model (COM) declara métodos sobrecarregados.

## <a name="rule-description"></a>Descrição da regra
Quando os métodos sobrecarregados são expostos a clientes COM, apenas a primeira sobrecarga do método mantém seu nome. Sobrecargas subsequentes são renomeadas exclusivamente anexando ao nome um caractere de sublinhado ' _ ' e um inteiro que corresponde à ordem de declaração da sobrecarga. Por exemplo, considere os seguintes métodos:

```csharp
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

Esses métodos são expostos a clientes COM como a seguir.

```csharp
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

Os clientes COM Visual Basic 6 não podem implementar métodos de interface usando um sublinhado no nome.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, renomeie os métodos sobrecarregados para que os nomes sejam exclusivos. Como alternativa, torne a interface invisível para COM alterando a acessibilidade para `internal` (`Friend` no [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou aplicando o conjunto de atributos <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> a `false`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma interface que viola a regra e uma interface que cumpre a regra.

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1413: evitar campos não públicos em tipos de valor visíveis em COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: evitar membros estáticos em tipos visíveis em COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
- [Tipo de Dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)
