---
title: 'CA1003: Usar instâncias do manipulador de eventos genéricos | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f8fbd3653043148513ec55fb18fdf211855a6d03
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58927816"
---
# <a name="ca1003-use-generic-event-handler-instances"></a>CA1003: Usar instâncias do manipulador de eventos genérico
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|UseGenericEventHandlerInstances|
|CheckId|CA1003|
|Categoria|Microsoft.Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo contém um delegado que retorna void, cuja assinatura contém dois parâmetros (o primeiro um objeto e o segundo um tipo atribuível a EventArgs) e os destinos de assembly contendo [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)].

## <a name="rule-description"></a>Descrição da Regra
 Antes de [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], para passar informações personalizadas para o manipulador de eventos, um novo delegado tinha que ser declarado que especificado de uma classe que deriva de <xref:System.EventArgs?displayProperty=fullName> classe. Isso não ocorre mais no [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)], que introduziu o <xref:System.EventHandler%601?displayProperty=fullName> delegar. Esse delegado genérico permite que qualquer classe que é derivada de <xref:System.EventArgs> a ser usado junto com o manipulador de eventos.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, remova o representante e substitua seu uso usando o <xref:System.EventHandler%601?displayProperty=fullName> delegar. Se o delegado é gerado automaticamente pelo [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] compilador, alterar a sintaxe da declaração de evento para usar o <xref:System.EventHandler%601?displayProperty=fullName> delegar.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um delegado que viola a regra. No [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] exemplo, comentários a seguir descrevem como modificar o exemplo para satisfazer a regra. Para obter o exemplo de C#, segue um exemplo que mostra o código modificado.

 [!code-csharp[FxCop.Design.CustomEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/cs/FxCop.Design.CustomEventHandler.cs#1)]
 [!code-vb[FxCop.Design.CustomEventHandler#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.CustomEventHandler/vb/FxCop.Design.CustomEventHandler.vb#1)]

## <a name="example"></a>Exemplo
 O exemplo a seguir remove a declaração de delegado do exemplo anterior, que satisfaz a regra e substitui seu uso na `ClassThatRaisesEvent` e `ClassThatHandlesEvent` métodos usando o <xref:System.EventHandler%601?displayProperty=fullName> delegar.

 [!code-csharp[FxCop.Design.GenericEventHandler#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.GenericEventHandler/cs/FxCop.Design.GenericEventHandler.cs#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1005: Evitar parâmetros excessivos em tipos genéricos](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)

 [CA1010: As coleções devem implementar a interface genérica](../code-quality/ca1010-collections-should-implement-generic-interface.md)

 [CA1000: Não declarar membros estáticos em tipos genéricos](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)

 [CA1002: Não expor listas genéricas](../code-quality/ca1002-do-not-expose-generic-lists.md)

 [CA1006: Não aninhar tipos genéricos em assinaturas de membro](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)

 [CA1004: Métodos genéricos devem fornecer o parâmetro de tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)

 [CA1007: Usar genéricos quando apropriado](../code-quality/ca1007-use-generics-where-appropriate.md)

## <a name="see-also"></a>Consulte também
 [Genéricos](http://msdn.microsoft.com/library/75ea8509-a4ea-4e7a-a2b3-cf72482e9282)
