---
title: 'CA2242: Testar para NaN corretamente'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 8912cb6eeec8009364936a42d572f4f3d83fae5e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919914"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testar para NaN corretamente

|||
|-|-|
|NomeDoTipo|TestForNaNCorrectly|
|CheckId|CA2242|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
Uma expressão testa um valor em <xref:System.Single.NaN?displayProperty=fullName> relação <xref:System.Double.NaN?displayProperty=fullName>a ou.

## <a name="rule-description"></a>Descrição da regra
 <xref:System.Double.NaN?displayProperty=fullName>, que representa não-um-Number, resulta quando uma operação aritmética é indefinida. Qualquer expressão que testa a igualdade entre um valor <xref:System.Double.NaN?displayProperty=fullName> e sempre `false`retorna. Qualquer expressão que testa desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna. `true`

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir uma violação dessa regra e determinar com precisão se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra duas expressões que testam um valor incorretamente <xref:System.Double.NaN?displayProperty=fullName> em relação a e uma expressão <xref:System.Double.IsNaN%2A?displayProperty=fullName> que o usa corretamente para testar o valor.

[!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
[!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]