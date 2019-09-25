---
title: 'CA2132: Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c5ca98219444515d01baf670489120238cb8dda
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232339"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base

|||
|-|-|
|NomeDoTipo|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Categoria|Microsoft.Security|
|Alteração significativa|Quebra|

> [!NOTE]
> Esse aviso é aplicado somente ao código que está executando o CoreCLR (a versão do CLR que é específica para aplicativos Web do Silverlight).

## <a name="cause"></a>Causa

O atributo Transparency do construtor padrão de uma classe derivada não é tão crítico quanto a transparência da classe base.

## <a name="rule-description"></a>Descrição da regra

Tipos e membros que não podem <xref:System.Security.SecurityCriticalAttribute> ser usados pelo código do aplicativo do Silverlight. Os tipos de segurança crítica e os membros só podem ser usados por código confiável no .NET Framework para a biblioteca de classes do Silverlight. Como uma construção pública ou protegida em uma classe derivada deve ter a mesma transparência maior que sua classe base, uma classe em um aplicativo não pode ser derivada de uma classe marcada como SecurityCritical.

Para o código de plataforma do CoreCLR, se um tipo base tiver um construtor padrão público ou não Transparent protegido, o tipo derivado deverá obedecer às regras de herança de construtor padrão. O tipo derivado também deve ter um construtor padrão e esse construtor deve ser, pelo menos, como construtor padrão crítico do tipo base.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir a violação, remova o tipo ou não derive do tipo de segurança não transparente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprimir avisos desta regra. As violações dessa regra pelo código do aplicativo resultarão na recusa do CoreCLR para carregar o tipo com um <xref:System.TypeLoadException>.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]