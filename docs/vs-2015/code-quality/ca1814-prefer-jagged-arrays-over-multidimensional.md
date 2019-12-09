---
title: 'CA1814: prefira matrizes denteadas em multidimensionais | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
helpviewer_keywords:
- PreferJaggedArraysOverMultidimensional
- CA1814
ms.assetid: b1ccf563-2ec8-42e5-b89c-731a9de1ea1d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f0ac183321bd2a3070b1f1ddc54402b74c8fb823
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668413"
---
# <a name="ca1814-prefer-jagged-arrays-over-multidimensional"></a>CA1814: preferir matrizes denteadas em relação às multidimensionais
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|PreferJaggedArraysOverMultidimensional|
|CheckId|CA1814|
|Categoria|Microsoft. performance|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um membro é declarado como uma matriz multidimensional.

## <a name="rule-description"></a>Descrição da Regra
 Uma matriz denteada é uma matriz cujos elementos são matrizes. As matrizes que constituem os elementos podem ter tamanhos diferentes, o que leva a menos espaço desperdiçado para alguns conjuntos de dados.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir uma violação dessa regra, altere a matriz multidimensional para uma matriz denteada.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Suprimir um aviso dessa regra se a matriz multidimensional não perder espaço.

## <a name="example"></a>Exemplo
 O exemplo a seguir mostra declarações para matrizes denteadas e multidimensionais.

 [!code-csharp[FxCop.Performance.JaggedArrays#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/cs/FxCop.Performance.JaggedArrays.cs#1)]
 [!code-vb[FxCop.Performance.JaggedArrays#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.JaggedArrays/vb/FxCop.Performance.JaggedArrays.vb#1)]
