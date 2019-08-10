---
title: 'CA2126: As demandas de link de tipo exigem demandas de herança'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
helpviewer_keywords:
- CA2126
- TypeLinkDemandsRequireInheritanceDemands
ms.assetid: 07b604e5-5579-4df9-a578-dadd0d8370a7
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2be42519f87c3c040c1f80c80d53d490853d986e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920760"
---
# <a name="ca2126-type-link-demands-require-inheritance-demands"></a>CA2126: As demandas de link de tipo exigem demandas de herança

|||
|-|-|
|NomeDoTipo|TypeLinkDemandsRequireInheritanceDemands|
|CheckId|CA2126|
|Categoria|Microsoft.Security|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
Um tipo não lacrado público é protegido com uma demanda de link, tem um método substituível e nem o tipo nem o método é protegido com uma demanda de herança.

## <a name="rule-description"></a>Descrição da regra
Uma demanda de link em um método ou seu tipo declarativo requer que o chamador imediato do método tenha a permissão especificada. Uma demanda de herança em um método requer que um método de substituição tenha a permissão especificada. Uma demanda de herança em um tipo exige que uma classe de derivação tenha a permissão especificada.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra, proteja o tipo ou o método com uma demanda de herança para a mesma permissão que a demanda de link.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra um tipo que viola a regra.

[!code-cpp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CPP/ca2126-type-link-demands-require-inheritance-demands_1.cpp)]
[!code-vb[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/VisualBasic/ca2126-type-link-demands-require-inheritance-demands_1.vb)]
[!code-csharp[FxCop.Security.TypesWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2126-type-link-demands-require-inheritance-demands_1.cs)]

## <a name="related-rules"></a>Regras relacionadas
[CA2108: Examinar a segurança declarativa em tipos de valor](../code-quality/ca2108-review-declarative-security-on-value-types.md)

[CA2112: Tipos protegidos não devem expor campos](../code-quality/ca2112-secured-types-should-not-expose-fields.md)

[CA2122: Não expor indiretamente métodos com demandas de link](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)

[CA2123: A substituição das demandas de link deve ser idêntica à base](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)

## <a name="see-also"></a>Consulte também

- [Diretrizes de codificação segura](/dotnet/standard/security/secure-coding-guidelines)
- [Demandas de link](/dotnet/framework/misc/link-demands)