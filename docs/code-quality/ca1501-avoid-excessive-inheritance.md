---
title: 'CA1501: Evitar herança excessiva'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 88464effce80b6957dc8945ad17f5a39b4f449c8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234514"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Evitar herança excessiva

|||
|-|-|
|NomeDoTipo|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Categoria|Microsoft.Maintainability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo está mais de quatro níveis abaixo na hierarquia de herança.

## <a name="rule-description"></a>Descrição da regra

As hierarquias de tipo profundamente aninhado podem ser difíceis de seguir, compreender e manter. Essa regra limita a análise a hierarquias no mesmo módulo.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir uma violação dessa regra, derive o tipo de um tipo base que seja menos profundo na hierarquia de herança ou elimine alguns dos tipos base intermediários.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

É seguro suprimir um aviso dessa regra. No entanto, o código pode ser mais difícil de manter. Observe que, dependendo da visibilidade dos tipos base, a resolução de violações dessa regra pode criar alterações significativas. Por exemplo, a remoção de tipos base públicos é uma alteração significativa.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra um tipo que viola a regra:

[!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/CSharp/ca1501-avoid-excessive-inheritance_1.cs)]
[!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../code-quality/codesnippet/VisualBasic/ca1501-avoid-excessive-inheritance_1.vb)]