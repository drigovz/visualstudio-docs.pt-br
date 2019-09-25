---
title: 'CA1405: Tipos base de tipo visível no COM devem ser visíveis no COM'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
helpviewer_keywords:
- CA1405
- ComVisibleTypeBaseTypesShouldBeComVisible
ms.assetid: a762ea2f-5285-4f73-bfb9-9eb10aea4290
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8e4e5c4ed258bcc88fedbb6d015fed576d326a0f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234964"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Tipos base de tipo visível no COM devem ser visíveis no COM

|||
|-|-|
|NomeDoTipo|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Categoria|Microsoft. Interoperability|
|Alteração significativa|DependsOnFix|

## <a name="cause"></a>Causa
Um tipo visível Component Object Model (COM) deriva de um tipo que não é visível COM.

## <a name="rule-description"></a>Descrição da regra
Quando um tipo visível COM adiciona membros em uma nova versão, ele deve obedecer a diretrizes estritas para evitar a interrupção de clientes COM que se associam à versão atual. Um tipo invisível para COM pressupõe que ele não precisa seguir essas regras de controle de versão COM ao adicionar novos membros. No entanto, se um tipo visível com for derivado do tipo invisível com e expor uma interface de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> classe <xref:System.Runtime.InteropServices.ClassInterfaceType> de ou (o padrão), todos os membros públicos do tipo base (a menos que eles estejam especificamente marcados como com invisível, o que seria redundante) são expostos a COM. Se o tipo base adicionar novos membros em uma versão subsequente, todos os clientes COM que se associarem à interface de classe do tipo derivado poderão ser interrompidos. Tipos visíveis COM devem derivar somente de tipos visíveis COM para reduzir a chance de quebrar clientes COM.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, torne os tipos base COM visíveis ou o tipo derivado COM invisível.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
[!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)