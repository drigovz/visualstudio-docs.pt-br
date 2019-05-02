---
title: 'CA2123: As demandas de link de substituição devem ser idênticas à base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52959279bca5aa0f86722050f6118f64997a901d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62545037"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: As demandas de link de substituição devem ser idênticas à base

|||
|-|-|
|NomeDoTipo|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público ou substitui um método implementa uma interface e não tem o mesmo [demandas de Link](/dotnet/framework/misc/link-demands) como a interface ou método virtual.

## <a name="rule-description"></a>Descrição da regra
 Esta regra compara um método ao método de base, que é uma interface ou um método virtual em outro tipo e, em seguida, compara as exigências de vínculo em cada um. Uma violação será relatada se o método ou o método base tem uma demanda de link e o outro não.

 Se essa regra for violada, um chamador mal-intencionado poderá ignorar a demanda de link simplesmente chamando o método não seguro.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra, aplica a mesma demanda de link para o método de substituição ou implementação. Se isso não é possível marcar o método com uma demanda completa ou remova o atributo completamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra as diversas violações dessa regra.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Demandas de link](/dotnet/framework/misc/link-demands)