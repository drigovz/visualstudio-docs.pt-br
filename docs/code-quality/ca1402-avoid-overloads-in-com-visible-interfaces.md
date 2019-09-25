---
title: 'CA1402: Evitar sobrecargas em interfaces visíveis no COM'
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
ms.openlocfilehash: fdbb6012fb1252c90014ba91caf8ad7dacf901c2
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234854"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evitar sobrecargas em interfaces visíveis no COM

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
Para corrigir uma violação dessa regra, renomeie os métodos sobrecarregados para que os nomes sejam exclusivos. Como alternativa, torne a interface invisível para com alterando a acessibilidade para `internal` (`Friend` em [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) ou aplicando o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> atributo definido como `false`.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra uma interface que viola a regra e uma interface que cumpre a regra.

[!code-vb[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/VisualBasic/ca1402-avoid-overloads-in-com-visible-interfaces_1.vb)]
[!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../code-quality/codesnippet/CSharp/ca1402-avoid-overloads-in-com-visible-interfaces_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA1413: Evitar campos não públicos em tipos de valores visíveis COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Evitar membros estáticos em tipos visíveis COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
- [Tipo de Dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)