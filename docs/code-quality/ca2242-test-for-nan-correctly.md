---
title: 'CA2242: Testar para NaN corretamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c809e6fe21bae15fed8c79c03a9210d518c157a3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838630"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testar para NaN corretamente

|||
|-|-|
|NomeDoTipo|TestForNaNCorrectly|
|CheckId|CA2242|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Uma expressão testa um valor em <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da regra
 <xref:System.Double.NaN?displayProperty=fullName>, que representa não é um número, o que resulta quando uma operação aritmética é indefinida. Qualquer expressão que testa a igualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `false`. Qualquer expressão que testa a desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `true`.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir uma violação dessa regra e determinar com precisão se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas expressões que testam incorretamente um valor em relação ao <xref:System.Double.NaN?displayProperty=fullName> e uma expressão que usa corretamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

 [!code-vb[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/VisualBasic/ca2242-test-for-nan-correctly_1.vb)]
 [!code-csharp[FxCop.Usage.TestForNaN#1](../code-quality/codesnippet/CSharp/ca2242-test-for-nan-correctly_1.cs)]