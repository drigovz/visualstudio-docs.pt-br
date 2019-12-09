---
title: 'CA1002: não expor listas genéricas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotExposeGenericLists
- CA1002
helpviewer_keywords:
- CA1002
- DoNotExposeGenericLists
ms.assetid: 5caac810-1a79-47df-a27b-c46c5040bf34
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2a1d8ea70ca86cbb2f38afff48fe37b414b70e88
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646309"
---
# <a name="ca1002-do-not-expose-generic-lists"></a>CA1002: não expor listas genéricas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotExposeGenericLists|
|CheckId|CA1002|
|Categoria|Microsoft. Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo contém um membro visível externamente que é um tipo de <xref:System.Collections.Generic.List%601?displayProperty=fullName>, retorna um tipo de <xref:System.Collections.Generic.List%601?displayProperty=fullName> ou cuja assinatura inclui um parâmetro <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Collections.Generic.List%601?displayProperty=fullName> é uma coleção genérica projetada para desempenho e não para herança. <xref:System.Collections.Generic.List%601?displayProperty=fullName> não contém membros virtuais que facilitam a alteração do comportamento de uma classe herdada. As coleções genéricas a seguir são projetadas para herança e devem ser expostas em vez de <xref:System.Collections.Generic.List%601?displayProperty=fullName>.

- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=fullName>

- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere o tipo de <xref:System.Collections.Generic.List%601?displayProperty=fullName> para uma das coleções genéricas projetadas para herança.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso dessa regra, a menos que o assembly que gera esse aviso não seja uma biblioteca reutilizável. Por exemplo, seria seguro suprimir esse aviso em um aplicativo ajustado para o desempenho em que um benefício de desempenho foi obtido do uso de listas genéricas.

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1003: usar instâncias do manipulador de eventos genéricos](../code-quality/ca1003-use-generic-event-handler-instances.md)

 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
