---
title: 'CA1003: usar instâncias de manipulador de eventos genéricas | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseGenericEventHandlerInstances
- CA1003
helpviewer_keywords:
- CA1003
- UseGenericEventHandlerInstances
ms.assetid: 402101b6-555d-4cf7-b223-1d9fdfaaf1cd
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 34318d3fb01f3f8dee50da2bc534908cecbdaf32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646295"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: usar instâncias do manipulador de eventos genéricos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Categoria|Microsoft. Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo contém um delegado que retorna void, cuja assinatura contém dois parâmetros (o primeiro objeto e o segundo, que pode ser atribuído a EventArgs), e os destinos de assembly que os contêm [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descrição da Regra
 Antes de [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], para passar informações personalizadas para o manipulador de eventos, um novo delegado tinha de ser declarado que especificou uma classe que era derivada da classe <xref:System.EventArgs?displayProperty=fullName>. Isso não é mais verdadeiro no [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], que introduziu o delegado de <xref:System.EventHandler%601?displayProperty=fullName>. Esse delegado genérico permite que qualquer classe derivada de <xref:System.EventArgs> seja usada junto com o manipulador de eventos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o delegado e substitua seu uso usando o <xref:System.EventHandler%601?displayProperty=fullName> delegado. Se o delegado for gerado automaticamente pelo compilador [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], altere a sintaxe da declaração de evento para usar o delegado <xref:System.EventHandler%601?displayProperty=fullName>.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um delegado que viola a regra. No exemplo a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], os comentários descrevem como modificar o exemplo para atender à regra. Para o C# exemplo, um exemplo a seguir mostra o código modificado.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir remove a declaração delegate do exemplo anterior, que satisfaz a regra e substitui seu uso nos métodos `ClassThatRaisesEvent` e `ClassThatHandlesEvent` usando o delegado <xref:System.EventHandler%601?displayProperty=fullName>.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: as coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: os métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](https://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
