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
ms.openlocfilehash: 8ba13514ca886ab822367bbd61aaebdc8527ec45
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945165"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Construtores padrão devem ser pelo menos tão críticos quanto construtores padrão do tipo base

|||
|-|-|
|NomeDoTipo|DefaultConstructorsMustHaveConsistentTransparency|
|CheckId|CA2132|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

> [!NOTE]
> Esse aviso só será aplicado ao código que está executando o CoreCLR (a versão do CLR que é específico para aplicativos web do Silverlight).

## <a name="cause"></a>Causa

O atributo de transparência do construtor padrão de uma classe derivada não é tão crítico quanto a transparência da classe base.

## <a name="rule-description"></a>Descrição da regra

Tipos e membros que têm o <xref:System.Security.SecurityCriticalAttribute> não pode ser usado pelo código do aplicativo do Silverlight. Os tipos de segurança crítica e os membros só podem ser usados por código confiável no .NET Framework para a biblioteca de classes do Silverlight. Como uma construção pública ou protegida em uma classe derivada deve ter a mesma transparência maior que sua classe base, uma classe em um aplicativo não pode ser derivada de uma classe marcada como SecurityCritical.

Para o código de plataforma do CoreCLR, se um tipo base tem um construtor público ou protegido padrão não transparente, em seguida, o tipo derivado deve obedecer as regras de herança do construtor padrão. O tipo derivado também deve ter um construtor padrão e esse construtor deve ser pelo menos construtor crítica do padrão do tipo base.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir a violação, remova o tipo ou não derivam de tipo não transparente de segurança.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Não suprima avisos dessa regra. As violações dessa regra pelo código do aplicativo resultará no CoreCLR se recusando a carregar o tipo com um <xref:System.TypeLoadException>.

### <a name="code"></a>Código

[!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]