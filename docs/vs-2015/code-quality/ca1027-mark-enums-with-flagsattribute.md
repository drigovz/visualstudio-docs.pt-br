---
title: 'CA1027: marcar enums com FlagsAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkEnumsWithFlags
- CA1027
helpviewer_keywords:
- CA1027
- MarkEnumsWithFlags
ms.assetid: 249e882c-8cd1-4c00-a2de-7b6bdc1849ff
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6f2dc7dcd79fbcaf47a2db3cf49f22f3467a06ab
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661929"
---
# <a name="ca1027-mark-enums-with-flagsattribute"></a>CA1027: marcar enums com FlagsAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkEnumsWithFlags|
|CheckId|CA1027|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Os valores de uma enumeração pública são potências de duas ou são combinações de outros valores que são definidos na enumeração e o atributo <xref:System.FlagsAttribute?displayProperty=fullName> não está presente. Para reduzir os falsos positivos, essa regra não relata uma violação das enumerações que têm valores contíguos.

## <a name="rule-description"></a>Descrição da Regra
 Uma enumeração é um tipo de valor que define um conjunto de constantes nomeadas relacionadas. Aplique <xref:System.FlagsAttribute> a uma enumeração quando suas constantes nomeadas puderem ser combinadas de uma significativa. Por exemplo, considere uma enumeração dos dias da semana em um aplicativo que controla quais recursos do dia estão disponíveis. Se a disponibilidade de cada recurso for codificada usando a enumeração que tem <xref:System.FlagsAttribute> presente, qualquer combinação de dias poderá ser representada. Sem o atributo, somente um dia da semana pode ser representado.

 Para campos que armazenam enumerações combináveis, os valores de enumeração individuais são tratados como grupos de bits no campo. Portanto, esses campos são, às vezes, chamados de *campos de bits*. Para combinar valores de enumeração para armazenamento em um campo de bits, use os operadores condicionais boolianos. Para testar um campo de bits para determinar se um valor de enumeração específico está presente, use os operadores lógicos boolianos. Para um campo de bits armazenar e recuperar valores de enumeração combinados corretamente, cada valor definido na enumeração deve ser uma potência de dois. A menos que isso seja feito, os operadores lógicos boolianos não poderão extrair os valores de enumeração individuais que são armazenados no campo.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, adicione <xref:System.FlagsAttribute> à enumeração.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso dessa regra se você não quiser que os valores de enumeração sejam combináveis.

## <a name="example"></a>Exemplo
 No exemplo a seguir, `DaysEnumNeedsFlags` é uma enumeração que atende aos requisitos para usar <xref:System.FlagsAttribute>, mas não tem. A enumeração `ColorEnumShouldNotHaveFlag` não tem valores que são potências de dois, mas especifica incorretamente <xref:System.FlagsAttribute>. Isso viola a regra [CA2217: não marque enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md).

 [!code-csharp[FxCop.Design.EnumFlags#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumFlags/cs/FxCop.Design.EnumFlags.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.FlagsAttribute?displayProperty=fullName>
