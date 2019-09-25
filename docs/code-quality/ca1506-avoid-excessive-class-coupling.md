---
title: 'CA1506: Evitar acoplamento de classes excessivo'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidExcessiveClassCoupling
- CA1506
helpviewer_keywords:
- AvoidExcessiveClassCoupling
- CA1506
ms.assetid: 9f0943c0-e802-4e3f-8798-2ab8653ddc80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1721fd52c00c5b312c88f19d48b668b12d28f050
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234488"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitar acoplamento de classes excessivo

|||
|-|-|
|NomeDoTipo|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Categoria|Microsoft.Maintainability|
|Alteração significativa|Quebra|

## <a name="cause"></a>Causa

Um tipo ou método é combinado com muitos outros tipos.

## <a name="rule-description"></a>Descrição da regra

Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.

Tipos e métodos que têm um alto grau de acoplamento de classe podem ser difíceis de manter. É uma boa prática ter tipos e métodos que apresentam baixo acoplamento e alta coesão.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir essa violação, tente recriar o tipo ou o método para reduzir o número de tipos aos quais ele está acoplado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Exclua este aviso quando o tipo ou método for considerado passível de manutenção, apesar de seu grande número de dependências em outros tipos.

## <a name="see-also"></a>Consulte também

- [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)
- [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)