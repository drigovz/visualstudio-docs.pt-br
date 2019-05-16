---
title: 'CA2123: As demandas de link de substituição devem ser idênticas à base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 338d61db9c24972b7fef656498abd43f8ea0b976
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687216"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: As demandas de link de substituição devem ser idênticas à base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um método público ou protegido em um tipo público ou substitui um método implementa uma interface e não tem o mesmo [demandas de Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) como a interface ou método virtual.

## <a name="rule-description"></a>Descrição da Regra
 Esta regra compara um método ao método de base, que é uma interface ou um método virtual em outro tipo e, em seguida, compara as exigências de vínculo em cada um. Uma violação será relatada se o método ou o método base tem uma demanda de link e o outro não.

 Se essa regra for violada, um chamador mal-intencionado poderá ignorar a demanda de link simplesmente chamando o método não seguro.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, aplica a mesma demanda de link para o método de substituir ou a implementação. Se isso não é possível marcar o método com uma demanda completa ou remova o atributo completamente.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra as diversas violações dessa regra.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.OverridesAndSecurity/cs/FxCop.Security.OverridesAndSecurity.cs#1)]

## <a name="see-also"></a>Consulte também
 [Diretrizes de codificação segura](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [demandas de Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)
