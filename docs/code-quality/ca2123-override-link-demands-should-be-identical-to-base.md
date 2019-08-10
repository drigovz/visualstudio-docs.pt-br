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
ms.openlocfilehash: 0ecc30f3fe16b283c0eb9cc1f369458bb1d7f952
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920806"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: As demandas de link de substituição devem ser idênticas à base

|||
|-|-|
|NomeDoTipo|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um método público ou protegido em um tipo público substitui um método ou implementa uma interface e não tem as mesmas demandas de [link](/dotnet/framework/misc/link-demands) que a interface ou o método virtual.

## <a name="rule-description"></a>Descrição da regra
Esta regra compara um método ao método de base, que é uma interface ou um método virtual em outro tipo e, em seguida, compara as exigências de vínculo em cada um. Uma violação será relatada se o método ou o método base tiver uma demanda de link e o outro não.

Se essa regra for violada, um chamador mal-intencionado poderá ignorar a demanda de link simplesmente chamando o método desprotegido.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, aplique a mesma demanda de link ao método ou implementação de substituição. Se isso não for possível, marque o método com uma demanda completa ou remova o atributo completamente.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra várias violações dessa regra.

[!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Demandas de link](/dotnet/framework/misc/link-demands)