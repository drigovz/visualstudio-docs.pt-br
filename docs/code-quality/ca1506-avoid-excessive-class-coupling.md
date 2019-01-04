---
title: 'CA1506: Evitar acoplamento de classes excessivo'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aa8d2e85ebacdedfde9d6731ff3e24a557de3e13
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53988550"
---
# <a name="ca1506-avoid-excessive-class-coupling"></a>CA1506: Evitar acoplamento de classes excessivo

|||
|-|-|
|NomeDoTipo|AvoidExcessiveClassCoupling|
|CheckId|CA1506|
|Categoria|Microsoft.Maintainability|
|Alteração Significativa|Quebra|

## <a name="cause"></a>Causa
 Um tipo ou método é acoplado com muitos outros tipos.

## <a name="rule-description"></a>Descrição da regra
 Esta regra mede o acoplamento de classes contando o número de referências de tipo exclusivas que um tipo ou um método contém.

 Tipos e métodos que têm um alto grau de acoplamento de classes podem ser difícil de manter. É uma boa prática tem tipos e métodos que apresentam menor acoplamento e maior coesão.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Para corrigir essa violação, tente recriar o tipo ou método para reduzir o número de tipos para o qual ele está acoplado.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
 Exclua esse aviso quando o tipo ou método ainda é considerado sustentável, apesar de seu grande número de dependências em outros tipos.

## <a name="see-also"></a>Consulte também

- [Avisos de facilidade de manutenção](../code-quality/maintainability-warnings.md)
- [Medindo complexidade e facilidade de manutenção do código gerenciado](../code-quality/code-metrics-values.md)