---
title: 'CA1018: marcar atributos com AttributeUsageAttribute | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 404ef250726d12300e2b72150ff42b4f0b7bfb24
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662046"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: marcar atributos com AttributeUsageAttribute
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Categoria|Microsoft. Design|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 O atributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> não está presente no atributo personalizado.

## <a name="rule-description"></a>Descrição da Regra
 Quando você define um atributo personalizado, marque-o usando <xref:System.AttributeUsageAttribute> para indicar onde no código-fonte o atributo personalizado pode ser aplicado. O significado e o uso desejado de um atributo determinarão seus locais válidos no código. Por exemplo, você pode definir um atributo que identifica a pessoa responsável por manter e aprimorar cada tipo em uma biblioteca, e essa responsabilidade sempre é atribuída no nível de tipo. Nesse caso, os compiladores devem habilitar o atributo em classes, enumerações e interfaces, mas não devem habilitá-lo em métodos, eventos ou propriedades. Procedimentos e políticas organizacionais ditariam se o atributo deveria ser habilitado em assemblies.

 A enumeração <xref:System.AttributeTargets?displayProperty=fullName> define os destinos que você pode especificar para um atributo personalizado. Se você omitir <xref:System.AttributeUsageAttribute>, seu atributo personalizado será válido para todos os destinos, conforme definido pelo valor de `All` da enumeração <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, especifique destinos para o atributo usando <xref:System.AttributeUsageAttribute>. Consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Você deve corrigir uma violação dessa regra em vez de excluir a mensagem. Mesmo que o atributo herde <xref:System.AttributeUsageAttribute>, o atributo deve estar presente para simplificar a manutenção do código.

## <a name="example"></a>Exemplo
 O exemplo a seguir define dois atributos. `BadCodeMaintainerAttribute` omite incorretamente a instrução <xref:System.AttributeUsageAttribute> e `GoodCodeMaintainerAttribute` implementa corretamente o atributo descrito anteriormente nesta seção. Observe que a propriedade `DeveloperName` é exigida pela regra de design [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md) e está incluído para fins de integridade.

 [!code-csharp[FxCop.Design.AttributeUsage#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/cs/FxCop.Design.AttributeUsage.cs#1)]
 [!code-vb[FxCop.Design.AttributeUsage#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.AttributeUsage/vb/FxCop.Design.AttributeUsage.vb#1)]

## <a name="related-rules"></a>Regras relacionadas
 [CA1019: definir acessadores para argumentos de atributo](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)

 [CA1813: evitar atributos não lacrados](../code-quality/ca1813-avoid-unsealed-attributes.md)

## <a name="see-also"></a>Consulte também
 [Atributos](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b)
