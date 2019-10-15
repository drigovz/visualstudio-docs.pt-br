---
title: 'CA1018: Marcar atributos com AttributeUsageAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
helpviewer_keywords:
- CA1018
- MarkAttributesWithAttributeUsage
ms.assetid: 6ab70ec0-220f-4880-af31-45067703133c
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 133ee073398817c037af95e2009c5acc98e1e5a2
ms.sourcegitcommit: 034c503ae04e22cf840ccb9770bffd012e40fb2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2019
ms.locfileid: "72306128"
---
# <a name="ca1018-mark-attributes-with-attributeusageattribute"></a>CA1018: Marcar atributos com AttributeUsageAttribute

|||
|-|-|
|NomeDoTipo|MarkAttributesWithAttributeUsage|
|CheckId|CA1018|
|Categoria|Microsoft.Design|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
O atributo <xref:System.AttributeUsageAttribute?displayProperty=fullName> não está presente no atributo personalizado.

## <a name="rule-description"></a>Descrição da regra
Quando você define um atributo personalizado, marque-o usando <xref:System.AttributeUsageAttribute> para indicar onde no código-fonte o atributo personalizado pode ser aplicado. O significado e o uso desejado de um atributo determinarão seus locais válidos no código. Por exemplo, você pode definir um atributo que identifica a pessoa responsável por manter e aprimorar cada tipo em uma biblioteca, e essa responsabilidade sempre é atribuída no nível de tipo. Nesse caso, os compiladores devem habilitar o atributo em classes, enumerações e interfaces, mas não devem habilitá-lo em métodos, eventos ou propriedades. Procedimentos e políticas organizacionais ditariam se o atributo deveria ser habilitado em assemblies.

A enumeração <xref:System.AttributeTargets?displayProperty=fullName> define os destinos que você pode especificar para um atributo personalizado. Se você omitir <xref:System.AttributeUsageAttribute>, seu atributo personalizado será válido para todos os destinos, conforme definido pelo valor de `All` da enumeração <xref:System.AttributeTargets>.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, especifique destinos para o atributo usando <xref:System.AttributeUsageAttribute>. Consulte o exemplo a seguir.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Você deve corrigir uma violação dessa regra em vez de excluir a mensagem. Mesmo que o atributo herde <xref:System.AttributeUsageAttribute>, o atributo deve estar presente para simplificar a manutenção do código.

## <a name="example"></a>Exemplo
O exemplo a seguir define dois atributos. `BadCodeMaintainerAttribute` omite incorretamente a instrução <xref:System.AttributeUsageAttribute> e `GoodCodeMaintainerAttribute` implementa corretamente o atributo descrito anteriormente nesta seção. Observe que a propriedade `DeveloperName` é exigida pela regra de design [CA1019: Defina os acessadores para os argumentos de atributo @ no__t-0 e estão incluídos para fins de integridade.

[!code-csharp[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/CSharp/ca1018-mark-attributes-with-attributeusageattribute_1.cs)]
[!code-vb[FxCop.Design.AttributeUsage#1](../code-quality/codesnippet/VisualBasic/ca1018-mark-attributes-with-attributeusageattribute_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1019: Definir acessadores para argumentos de atributo @ no__t-0

[CA1813: Evitar atributos não lacrados @ no__t-0

## <a name="see-also"></a>Consulte também

- [Atributos](/dotnet/standard/design-guidelines/attributes)