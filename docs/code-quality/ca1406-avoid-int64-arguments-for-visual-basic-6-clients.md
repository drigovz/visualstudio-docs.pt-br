---
title: 'CA1406: Evitar argumentos Int64 para clientes do Visual Basic 6'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
helpviewer_keywords:
- AvoidInt64ArgumentsForVB6Clients
- CA1406
ms.assetid: d5d0d3fc-f105-43da-be5b-923ab023309c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 82a8b1ea389c37dc63a9fe7366208a2a3028efb8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234809"
---
# <a name="ca1406-avoid-int64-arguments-for-visual-basic-6-clients"></a>CA1406: Evitar argumentos Int64 para clientes do Visual Basic 6

|||
|-|-|
|NomeDoTipo|AvoidInt64ArgumentsForVB6Clients|
|CheckId|CA1406|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo marcado especificamente como visível para Component Object Model (com) declara um membro que usa um <xref:System.Int64?displayProperty=fullName> argumento.

## <a name="rule-description"></a>Descrição da regra
Os clientes COM do Visual Basic 6 não podem acessar inteiros de 64 bits.

Por padrão, os itens a seguir são visíveis para COM: assemblies, tipos públicos, membros de instância pública em tipos públicos e todos os membros de tipos de valor público. No entanto, para reduzir os falsos positivos, essa regra exige que a visibilidade COM do tipo seja explicitamente declarada; o assembly contentor deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra para um parâmetro cujo valor sempre pode ser expresso como um integral de 32 bits, altere o tipo de parâmetro para <xref:System.Int32?displayProperty=fullName>. Se o valor do parâmetro puder ser maior do que pode ser expresso como um integral de 32 bits, altere o tipo de parâmetro <xref:System.Decimal?displayProperty=fullName>para. Observe que <xref:System.Single?displayProperty=fullName> e <xref:System.Double?displayProperty=fullName> perdem <xref:System.Int64> a precisão nos intervalos superiores do tipo de dados. Se o membro não for destinado a ser visível para com, marque-o com <xref:System.Runtime.InteropServices.ComVisibleAttribute> o conjunto `false`como.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se for certo que Visual Basic 6 clientes COM não acessarão o tipo.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-csharp[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/CSharp/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.cs)]
[!code-vb[FxCop.Interoperability.LongArgument#1](../code-quality/codesnippet/VisualBasic/ca1406-avoid-int64-arguments-for-visual-basic-6-clients_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1413: Evitar campos não públicos em tipos de valores visíveis COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

[CA1407: Evitar membros estáticos em tipos visíveis COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
- [Tipo de Dados Long](/dotnet/visual-basic/language-reference/data-types/long-data-type)