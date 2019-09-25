---
title: 'CA1403: Tipos de layout automático não devem ser visíveis no COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 4e590514247444d32d0d9a31b2bbc409434cf53c
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234829"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: Tipos de layout automático não devem ser visíveis no COM

|||
|-|-|
|NomeDoTipo|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo de valor visível Component Object Model (com) é marcado com <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> o atributo definido <xref:System.Runtime.InteropServices.LayoutKind.Auto?displayProperty=fullName>como.

## <a name="rule-description"></a>Descrição da regra

<xref:System.Runtime.InteropServices.LayoutKind>os tipos de layout são gerenciados pelo Common Language Runtime. O layout desses tipos pode ser alterado entre as versões do .NET, o que interrompe os clientes COM que esperam um layout específico. Se o <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo não for especificado, os C#compiladores, Visual Basic C++ e especificam [LayoutKind. auto](<xref:System.Runtime.InteropServices.LayoutKind.Auto>) para tipos de valor.

A menos que marcado de outra forma, todos os tipos públicos e não genéricos são visíveis para COM, e todos os tipos não públicos e genéricos são invisíveis para COM. No entanto, para reduzir os falsos positivos, essa regra requer que a visibilidade de COM do tipo seja explicitamente declarada. O assembly contentor deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, altere o valor do <xref:System.Runtime.InteropServices.StructLayoutAttribute> atributo para [LayoutKind. Explicit](<xref:System.Runtime.InteropServices.LayoutKind.Explicit>) ou [LayoutKind. Sequential](<xref:System.Runtime.InteropServices.LayoutKind.Sequential>)ou torne o tipo invisível para com.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaz a regra.

[!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
[!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]

## <a name="related-rules"></a>Regras relacionadas

[CA1408: Não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte também

- [Qualificar tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)
- [Interoperar com código não gerenciado](/dotnet/framework/interop/index)