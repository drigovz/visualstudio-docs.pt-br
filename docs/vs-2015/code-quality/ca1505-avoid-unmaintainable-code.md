---
title: 'CA1505: evitar código não passível de manutenção | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AvoidUnmaintainableCode
- CA1505
helpviewer_keywords:
- AvoidUnmaintainableCode
- CA1505
ms.assetid: 8292b268-5929-4221-b699-f9c414bcec5d
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 87aacfd675181e35d289b2a054c58f83f3f790fa
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607584"
---
# <a name="ca1505-avoid-unmaintainable-code"></a>CA1505: evitar código que não possa ser mantido
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|AvoidUnmantainableCode|
|CheckId|CA1505|
|Categoria|Microsoft. Maintainabilidade|
|Alteração Significativa|Sem interrupção|

## <a name="cause"></a>Causa
 Um tipo ou um método tem um baixo valor de índice de facilidade de manutenção.

## <a name="rule-description"></a>Descrição da Regra
 O índice de manutenção é calculado usando as seguintes métricas: linhas de código, volume de programas e complexidade ciclomática. O volume do programa é uma medida da dificuldade de compreender um tipo ou método com base no número de operadores e operandos no código. A complexidade de ciclomática é uma medida da complexidade estrutural do tipo ou do método. Você pode aprender mais sobre as métricas de código em [medindo a complexidade e a manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md).

 Um índice de manutenção baixa indica que um tipo ou método provavelmente é difícil de manter e seria um bom candidato para reformular.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir essa violação, Reprojete o tipo ou o método e tente dividi-lo em tipos ou métodos menores e mais focados.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Exclua este aviso quando um tipo ou método ainda for considerado passível de manutenção, apesar de seu tamanho grande, ou quando o tipo ou método não puder ser dividido.

## <a name="see-also"></a>Consulte também
 [Avisos de facilidade](../code-quality/maintainability-warnings.md) [de manutenção medindo a complexidade e a manutenção do código gerenciado](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
