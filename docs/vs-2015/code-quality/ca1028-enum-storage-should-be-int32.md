---
title: 'CA1028: Armazenamento de enum deve ser Int32 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1028
- EnumStorageShouldBeInt32
helpviewer_keywords:
- EnumStorageShouldBeInt32
- CA1028
ms.assetid: 87160825-9f39-4142-8d7f-a31fe7ac7b84
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e79eb7e0ed33184103cc772c13515959cf973ecc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68192804"
---
# <a name="ca1028-enum-storage-should-be-int32"></a>CA1028: O armazenamento de enumerações deve ser Int32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|EnumStorageShouldBeInt32|
|CheckId|CA1028|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O tipo subjacente de uma enumeração pública não é <xref:System.Int32?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Por padrão, o <xref:System.Int32?displayProperty=fullName> tipo de dados é usado para armazenar o valor da constante. Embora você possa alterar esse tipo subjacente, não é necessário ou recomendado na maioria dos cenários. Observe que nenhum ganho de desempenho significativa é obtido por meio de um tipo de dados é menor do que <xref:System.Int32>. Se você não pode usar o tipo de dados padrão, você deve usar um do sistema CLS (Common Language)-compatível com tipos integrais, <xref:System.Byte>, <xref:System.Int16>, <xref:System.Int32>, ou <xref:System.Int64> para certificar-se de que todos os valores da enumeração podem ser representados em Linguagens de programação compatíveis com CLS.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, a menos que haja problemas de compatibilidade ou de tamanho, use <xref:System.Int32>. Para situações em que <xref:System.Int32> não é grande o suficiente para manter os valores, use <xref:System.Int64>. Se a compatibilidade com versões anteriores requer um tipo de dados menor, use <xref:System.Byte> ou <xref:System.Int16>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprima um aviso nessa regra somente se os problemas de compatibilidade com versões anteriores a exige. Em aplicativos, falha em cumprir com esta regra geral, não causa problemas. Em bibliotecas, onde a interoperabilidade de linguagem é necessária, a não conformidade com esta regra poderá afetar negativamente seus usuários.

## <a name="example-of-a-violation"></a>Exemplo de uma violação

### <a name="description"></a>Descrição
 O exemplo a seguir mostra duas enumerações que não usam o tipo de dados subjacente recomendado.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/cs/FxCop.Design.EnumIntegralType.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralType#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralType/vb/FxCop.Design.EnumIntegralType.vb#1)]

## <a name="example-of-how-to-fix"></a>Exemplo de como a correção

### <a name="description"></a>Descrição
 O exemplo a seguir corrige a violação anterior, alterando o tipo de dados subjacente para <xref:System.Int32>.

### <a name="code"></a>Código
 [!code-csharp[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/cs/FxCop.Design.EnumIntegralTypeFixed.cs#1)]
 [!code-vb[FxCop.Design.EnumIntegralTypeFixed#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumIntegralTypeFixed/vb/FxCop.Design.EnumIntegralTypeFixed.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1008: Enums devem ter valor zero](../code-quality/ca1008-enums-should-have-zero-value.md)

 [CA1027: Marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

 [CA2217: Não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: Não nomeie valores de enumeração 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: Valores enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Byte?displayProperty=fullName> <xref:System.Int16?displayProperty=fullName>
 <xref:System.Int32?displayProperty=fullName>
 <xref:System.Int64?displayProperty=fullName>
