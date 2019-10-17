---
title: 'CA1506: evitar acoplamento de classes excessivo'
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
ms.openlocfilehash: c13e1ee9a0336cb6b91ab763f4fabb28ab9cb7c8
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440038"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: evitar acoplamento de classes excessivo

|||
|-|-|
|NomeDoTipo|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Categoria|Microsoft. Maintainabilidade|
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
