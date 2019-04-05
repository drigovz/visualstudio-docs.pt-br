---
title: 'CA2242: Testar para NaN corretamente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- TestForNaNCorrectly
- CA2242
helpviewer_keywords:
- CA2242
ms.assetid: e12dcffc-e255-4e1e-8fdf-3c6054d44abe
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 17a98ce3d213c5d9ae85bb5132a0a44e50112037
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922237"
---
# <a name="ca2242-test-for-nan-correctly"></a>CA2242: Testar para NaN corretamente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|TestForNaNCorrectly|
|CheckId|CA2242|
|Categoria|Microsoft.Usage|
|Alteração Significativa|Não separável|

## <a name="cause"></a>Causa
 Uma expressão testa um valor em <xref:System.Single.NaN?displayProperty=fullName> ou <xref:System.Double.NaN?displayProperty=fullName>.

## <a name="rule-description"></a>Descrição da Regra
 <xref:System.Double.NaN?displayProperty=fullName>, que representa não é um número, o que resulta quando uma operação aritmética é indefinida. Qualquer expressão que testa a igualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `false`. Qualquer expressão que testa a desigualdade entre um valor e <xref:System.Double.NaN?displayProperty=fullName> sempre retorna `true`.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra e determinar com precisão se um valor representa <xref:System.Double.NaN?displayProperty=fullName>, use <xref:System.Single.IsNaN%2A?displayProperty=fullName> ou <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprima um aviso nessa regra.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra duas expressões que testam incorretamente um valor em relação ao <xref:System.Double.NaN?displayProperty=fullName> e uma expressão que usa corretamente <xref:System.Double.IsNaN%2A?displayProperty=fullName> para testar o valor.

 [!code-csharp[FxCop.Usage.TestForNaN#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/cs/FxCop.Usage.TestForNaN.cs#1)]
 [!code-vb[FxCop.Usage.TestForNaN#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.TestForNaN/vb/FxCop.Usage.TestForNaN.vb#1)]
