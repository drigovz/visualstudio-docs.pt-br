---
title: 'CA1413: Evitar campos não públicos em tipos de valor visíveis no COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
helpviewer_keywords:
- CA1413
- AvoidNonpublicFieldsInComVisibleValueTypes
ms.assetid: 1352e7eb-fefc-4239-8847-25edc7804a54
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 0d4fed5b16120ec069eaa4101670c88ad8f3a247
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234645"
---
# <a name="ca1413-avoid-non-public-fields-in-com-visible-value-types"></a>CA1413: Evitar campos não públicos em tipos de valor visíveis no COM

|||
|-|-|
|NomeDoTipo|AvoidNonpublicFieldsInComVisibleValueTypes|
|CheckId|CA1413|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo de valor marcado especificamente como visível para Component Object Model (COM) declara um campo de instância não pública.

## <a name="rule-description"></a>Descrição da regra
Os campos de instância não pública dos tipos de valor visíveis por COM permanecem visíveis para clientes COM. Examine o conteúdo do campo para obter informações que não devem ser expostas, ou que terão um efeito de design ou segurança indesejado.

Por padrão, todos os tipos de valor público são visíveis para COM. No entanto, para reduzir os falsos positivos, essa regra requer que a visibilidade de COM do tipo seja explicitamente declarada. O assembly contentor deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> definido como `false` e o tipo deve ser marcado com o <xref:System.Runtime.InteropServices.ComVisibleAttribute> definido como `true`.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra e manter o campo oculto, altere o tipo de valor para um tipo de referência ou remova <xref:System.Runtime.InteropServices.ComVisibleAttribute> o atributo do tipo.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
É seguro suprimir um aviso dessa regra se a exposição pública do campo for aceitável.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-csharp[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/CSharp/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.cs)]
[!code-vb[FxCop.Interoperability.NonpublicField#1](../code-quality/codesnippet/VisualBasic/ca1413-avoid-non-public-fields-in-com-visible-value-types_1.vb)]

## <a name="related-rules"></a>Regras relacionadas
[CA1407: Evitar membros estáticos em tipos visíveis COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

[CA1017: Marcar assemblies com ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Consulte também

- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)
- [Qualificando tipos .NET para interoperação](/dotnet/framework/interop/qualifying-net-types-for-interoperation)