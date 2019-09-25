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
ms.openlocfilehash: 0e74ec49667a4fe66c399bd15e8b24aa6589ce88
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71237838"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testar para NaN corretamente

|||
|-|-|
|NomeDoTipo|TestForNaNCorrectly|
|CheckId|CA2242|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção|

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