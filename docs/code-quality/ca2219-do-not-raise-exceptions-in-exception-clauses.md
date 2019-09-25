---
title: 'CA2219: Não acionar exceções em cláusulas de exceção'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c06f8693034b9943de8072f110f4661b87098a5
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231149"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Não acionar exceções em cláusulas de exceção

|||
|-|-|
|NomeDoTipo|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Categoria|Microsoft.Usage|
|Alteração significativa|Sem interrupção, quebrando|

## <a name="cause"></a>Causa
Uma exceção é lançada de uma `finally`cláusula, filtro ou falha.

## <a name="rule-description"></a>Descrição da regra
Quando uma exceção é gerada em uma cláusula de exceção, aumenta muito a dificuldade de depuração.

Quando uma exceção é gerada em uma `finally` cláusula ou falha, a nova exceção oculta a exceção ativa, se presente. Isso torna o erro original difícil de detectar e depurar.

Quando uma exceção é gerada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção e faz com que o filtro seja avaliado como falso. Não há como dizer a diferença entre o filtro avaliando como falso e uma exceção sendo emitida de um filtro. Isso torna difícil detectar e depurar erros na lógica do filtro.

## <a name="how-to-fix-violations"></a>Como corrigir violações
Para corrigir essa violação dessa regra, não gere explicitamente uma exceção de uma `finally`cláusula, filtro ou falha.

## <a name="when-to-suppress-warnings"></a>Quando suprimir avisos
Não suprimir um aviso para esta regra. Não há cenários sob os quais uma exceção gerada em uma cláusula de exceção fornece um benefício para o código em execução.

## <a name="related-rules"></a>Regras relacionadas
[CA1065: Não gerar exceções em locais inesperados](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Consulte também
[Avisos de design](../code-quality/design-warnings.md)