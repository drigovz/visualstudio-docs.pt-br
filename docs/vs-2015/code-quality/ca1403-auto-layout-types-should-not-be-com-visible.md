---
title: 'CA1403: os tipos de layout automático não devem ser visíveis no COM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5f39540cb23d86dda4244604da8a9ff764594e11
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661333"
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: os tipos de layout automático não devem ser visíveis em COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AutoLayoutTypesShouldNotBeComVisible|
|CheckId|CA1403|
|Categoria|Microsoft. Interoperability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo de valor visível Component Object Model (COM) é marcado com o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> definido como <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 os tipos de layout <xref:System.Runtime.InteropServices.LayoutKind> são gerenciados pelo Common Language Runtime. O layout desses tipos pode ser alterado entre as versões do .NET Framework, o que interromperá clientes COM que esperam um layout específico. Observe que, se o atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> não for especificado, C#o, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] e C++ compiladores especificarão o layout de <xref:System.Runtime.InteropServices.LayoutKind> para tipos de valor.

 A menos que marcado de outra forma, todos os tipos públicos não genéricos são visíveis para COM; todos os tipos não públicos e genéricos são invisíveis para COM. No entanto, para reduzir os falsos positivos, essa regra exige que a visibilidade COM do tipo seja explicitamente declarada; o assembly contentor deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o valor do atributo <xref:System.Runtime.InteropServices.StructLayoutAttribute> para <xref:System.Runtime.InteropServices.LayoutKind> ou <xref:System.Runtime.InteropServices.LayoutKind> ou torne o tipo invisível para COM.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra e um tipo que satisfaz a regra.

 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/cs/FxCop.Interoperability.AutoLayout.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoLayout/vb/FxCop.Interoperability.AutoLayout.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1408: não usar AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Consulte também
 [Introdução à interface de classe](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [qualificando tipos .net para interoperação](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [interoperabilidade com código não-gerenciado](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
