---
title: 'CA2219: não gerar exceções nas cláusulas de exceção | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebce51d360518d1cc66f652714c59d27751586b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668876"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: não acione exceções em cláusulas de exceção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|NomeDoTipo|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Categoria|Microsoft. Usage|
|Alteração Significativa|Sem interrupção, quebra|

## <a name="cause"></a>Causa
 Uma exceção é gerada de uma cláusula `finally`, Filter ou Fault.

## <a name="rule-description"></a>Descrição da Regra
 Quando uma exceção é gerada em uma cláusula de exceção, aumenta muito a dificuldade de depuração.

 Quando uma exceção é gerada em uma cláusula `finally` ou Fault, a nova exceção oculta a exceção ativa, se presente. Isso torna o erro original difícil de detectar e depurar.

 Quando uma exceção é gerada em uma cláusula de filtro, o tempo de execução captura silenciosamente a exceção e faz com que o filtro seja avaliado como falso. Não há como dizer a diferença entre o filtro avaliando como falso e uma exceção sendo emitida de um filtro. Isso torna difícil detectar e depurar erros na lógica do filtro.

## <a name="how-to-fix-violations"></a>Como Corrigir Violações
 Para corrigir essa violação dessa regra, não gere explicitamente uma exceção de uma cláusula `finally`, Filter ou Fault.

## <a name="when-to-suppress-warnings"></a>Quando Suprimir Avisos
 Não suprimir um aviso para esta regra. Não há cenários sob os quais uma exceção gerada em uma cláusula de exceção fornece um benefício para o código em execução.

## <a name="related-rules"></a>Regras relacionadas
 [CA1065: não acionar exceções em locais inesperados](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Consulte também
 [Avisos de design](../code-quality/design-warnings.md)
