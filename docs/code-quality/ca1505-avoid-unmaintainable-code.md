---
title: 'CA1505: Evitar código de difícil manutenção'
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
ms.openlocfilehash: 740ef26af6f1f84d23ef27de5176df1b3de98b34
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232490"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: Evitar código de difícil manutenção

|||
|-|-|
|NomeDoTipo|AvoidUnmantainableCode|
|CheckId|CA1505|
|Categoria|Microsoft.Maintainability|
|Alteração Significativa|Não são significativas|

## <a name="cause"></a>Causa

Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção.

## <a name="rule-description"></a>Descrição da regra

O índice de facilidade de manutenção é calculado usando as seguintes métricas: linhas de código, o volume de programa e a complexidade ciclomática. Volume do programa é uma medida da dificuldade de compreensão de um tipo ou método que se baseia no número de operadores e operandos no código. A complexidade ciclomática é uma medida da complexidade estrutural do tipo ou método. Você pode aprender mais sobre as métricas de código em [medir a complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md).

Um índice de facilidade de manutenção baixa indica que um tipo ou método é provavelmente difícil de manter e seria um bom candidato para refazer o design.

## <a name="how-to-fix-violations"></a>Como corrigir violações

Para corrigir essa violação, recriar o tipo ou método e tente dividi-lo em menores e mais concentrados tipos ou métodos.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos

Você pode suprimir esse aviso quando o tipo ou método não pode ser dividido ou é considerado sustentável, apesar de seu tamanho grande.

## <a name="see-also"></a>Consulte também

- [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)
- [Medir a complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)