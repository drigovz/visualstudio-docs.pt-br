---
title: 'CA1405: Tipos base de tipo visível no COM devem ser visíveis no COM'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: a94654475432706592c3cd2845488163529ca260
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943215"
---
# <a name="ca1405-com-visible-type-base-types-should-be-com-visible"></a>CA1405: Tipos base de tipo visível no COM devem ser visíveis no COM

|||
|-|-|
|NomeDoTipo|ComVisibleTypeBaseTypesShouldBeComVisible|
|CheckId|CA1405|
|Categoria|Microsoft.Interoperability|
|Alteração Significativa|DependsOnFix|

## <a name="cause"></a>Causa
 Um tipo visível do modelo de objeto de componente (COM) deriva de um tipo que não é visível do COM.

## <a name="rule-description"></a>Descrição da regra
 Quando um tipo visível do COM adiciona membros em uma nova versão, ele deve obedecer as diretrizes rígidas para evitar a interrupção de clientes COM associados para a versão atual. Um tipo que é invisível para COM supõe que ele não precisa seguir estas regras de controle de versão de COM quando ele adiciona novos membros. No entanto, se um visíveis em COM tipo deriva de tipo invisível COM e expõe uma interface de classe de <xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName> ou <xref:System.Runtime.InteropServices.ClassInterfaceType> (padrão), todos os membros públicos do tipo base (a menos que eles são especificamente marcados COM como invisíveis, qual seria redundante) são exposto COM. Se o tipo base adiciona novos membros em uma versão posterior, podem interromper todos os clientes COM associados à interface de classe do tipo derivado. Tipos visíveis no COM devem derivar somente de tipos visíveis no COM para reduzir a chance de interromper os clientes COM.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, verifique os tipos base visíveis no COM ou o tipo derivado COM invisível.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra um tipo que viola a regra.

 [!code-vb[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/VisualBasic/ca1405-com-visible-type-base-types-should-be-com-visible_1.vb)]
 [!code-csharp[FxCop.Interoperability.ComBaseTypes#1](../code-quality/codesnippet/CSharp/ca1405-com-visible-type-base-types-should-be-com-visible_1.cs)]

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute?displayProperty=fullName>
- [Interoperação com código não gerenciado](/dotnet/framework/interop/index)