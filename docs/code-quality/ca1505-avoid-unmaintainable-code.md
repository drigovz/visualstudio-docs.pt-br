---
title: 'CA1505: evitar código que não possa ser mantido'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f39b6b909722c35edb16ebaf1cee43507f22215d
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440068"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitar código que não possa ser mantido

|||
|-|-|
|NomeDoTipo|AvoidUnmantainableCode|
|CheckId|CA1505|
|Categoria|Microsoft. Maintainabilidade|
|Alteração significativa|Sem interrupção|

## <a name="cause"></a>Causa

Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção.

## <a name="rule-description"></a>Descrição da regra

O índice de manutenção é calculado usando as seguintes métricas: linhas de código, volume de programas e complexidade ciclomática. O volume do programa é uma medida da dificuldade de entender um tipo ou método baseado no número de operadores e operandos no código. A complexidade de ciclomática é uma medida da complexidade estrutural do tipo ou do método. Você pode aprender mais sobre as métricas de código em [medir a complexidade e a manutenção do código gerenciado](../code-quality/code-metrics-values.md).

Um índice de manutenção baixa indica que um tipo ou método provavelmente é difícil de manter e seria um bom candidato para reformular.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir essa violação, Reprojete o tipo ou o método e tente dividi-lo em tipos ou métodos menores e mais focados.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você pode suprimir esse aviso quando o tipo ou método não puder ser dividido ou for considerado passível de manutenção, apesar de seu tamanho grande.

## <a name="see-also"></a>Consulte também

- [Avisos de manutenção](../code-quality/maintainability-warnings.md)
- [Medir complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)
