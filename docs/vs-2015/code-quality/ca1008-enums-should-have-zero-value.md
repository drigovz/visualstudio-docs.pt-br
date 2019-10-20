---
title: 'CA1008: Enums devem ter valor zero | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1008
- EnumsShouldHaveZeroValue
helpviewer_keywords:
- CA1008
- EnumsShouldHaveZeroValue
ms.assetid: 3503a73c-360c-416d-8ee4-c2aa44365a05
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: fbc7775d4ec41822b866868a6db6bceb353af989
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668927"
---
# <a name="ca1008-enums-should-have-zero-value"></a>CA1008: os enums devem ter valor zero
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|EnumsShouldHaveZeroValue|
|CheckId|CA1008|
|Categoria|Microsoft. Design|
|Alteração Significativa|Sem interrupção – quando você for solicitado a adicionar um valor **None** a uma enumeração sem sinalizador. Quebra-quando você é solicitado a renomear ou remover qualquer valor de enumeração.|

## <a name="cause"></a>Causa
 Uma enumeração sem um <xref:System.FlagsAttribute?displayProperty=fullName> aplicado não define um membro que tenha um valor de zero; ou uma enumeração que tem um <xref:System.FlagsAttribute> aplicado define um membro que tem um valor igual a zero, mas seu nome não é ' none ' ou a enumeração define vários membros com valor zero.

## <a name="rule-description"></a>Descrição da Regra
 O valor padrão de uma enumeração não inicializada, assim como outros tipos de valor, é zero. Um não sinalizadores − enumeração atribuída deve definir um membro que tenha o valor de zero para que o valor padrão seja um valor válido da enumeração. Se apropriado, nomeie o membro como "nenhum". Caso contrário, atribua zero ao membro usado com mais frequência. Observe que, por padrão, se o valor do primeiro membro de enumeração não estiver definido na declaração, seu valor será zero.

 Se uma enumeração que tem o <xref:System.FlagsAttribute> aplicado definir um membro com valor zero, seu nome deverá ser ' none ' para indicar que nenhum valor foi definido na enumeração. O uso de um membro de valor zero para qualquer outra finalidade é diferente do uso do <xref:System.FlagsAttribute> em que os operadores AND e OR não são inúteis com o membro. Isso implica que apenas um membro deve receber o valor zero. Observe que, se vários membros que têm o valor zero ocorrerem em uma enumeração atribuída por sinalizadores, `Enum.ToString()` retornará resultados incorretos para membros que não são zero.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação desta regra para não sinalizadores − enumerações atribuídas, defina um membro que tenha o valor de zero; Essa é uma alteração sem interrupção. Para enumerações atribuídas a sinalizadores que definem um membro com valor zero, nomeie este membro como ' none ' e exclua todos os outros membros que tenham um valor de zero; Essa é uma alteração significativa.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra, exceto para enumerações atribuídas a sinalizadores que foram enviadas anteriormente.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas enumerações que satisfazem a regra e uma enumeração, `BadTraceOptions`, que viola a regra.

 [!code-cpp[FxCop.Design.EnumsZeroValue#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cpp/FxCop.Design.EnumsZeroValue.cpp#1)]
 [!code-csharp[FxCop.Design.EnumsZeroValue#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/cs/FxCop.Design.EnumsZeroValue.cs#1)]
 [!code-vb[FxCop.Design.EnumsZeroValue#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EnumsZeroValue/vb/FxCop.Design.EnumsZeroValue.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA2217: não marcar enums com FlagsAttribute](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)

 [CA1700: não nomear valores de enum como 'Reservados'](../code-quality/ca1700-do-not-name-enum-values-reserved.md)

 [CA1712: não usar valores de enum como prefixo com o nome do tipo](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)

 [CA1028: o armazenamento de enum deve ser Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)

 [CA1027: marcar enums com FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)

## <a name="see-also"></a>Consulte também
 <xref:System.Enum?displayProperty=fullName>
