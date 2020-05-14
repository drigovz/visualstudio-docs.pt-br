---
title: Arquitetura avaliadora de expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, expression evaluators
- expression evaluators, architecture
- debugging [Debugging SDK], expression evaluators
ms.assetid: aad7c4c6-1dc1-4d32-b975-f1fdf76bdeda
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aac782c653f230d5598a49d43eb70f548de6dc41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738701"
---
# <a name="expression-evaluator-architecture"></a>Arquitetura avaliadora de expressão
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Integrar uma linguagem proprietária no pacote de depuração do Visual Studio significa que você deve configurar as interfaces de avaliador de expressão (EE) necessárias e chamar o provedor de símbolos de tempo de execução (SP) e interfaces de encadernação da linguagem comum. Os objetos SP e binder, juntamente com o endereço de execução atual, são o contexto em que as expressões são avaliadas. As informações que essas interfaces produzem e consomem representam os conceitos-chave na arquitetura de um EE.

## <a name="overview"></a>Visão geral

### <a name="parse-the-expression"></a>Analisar a Expressão
 Quando você está depurando um programa, as expressões são avaliadas por uma série de razões, mas sempre quando o programa está sendo depurado foi interrompido em um ponto de ruptura (seja um ponto de ruptura colocado pelo usuário ou um causado por uma exceção). É neste momento que o Visual Studio obtém um quadro de pilha, representado pela interface [IDebugStackFrame2,](../../extensibility/debugger/reference/idebugstackframe2.md) do mecanismo de depuração (DE). O Visual Studio então chama [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter a interface [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) Esta interface representa um contexto no qual as expressões podem ser avaliadas; [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) é o ponto de entrada para o processo de avaliação. Até este ponto, todas as interfaces são implementadas pelo DE.

 Quando `IDebugExpressionContext2::ParseText` é chamado, o DE instancia o EE associado à linguagem do arquivo de origem onde ocorreu o ponto de ruptura (o DE também instancia o SH neste momento). O EE é representado pela interface [IDebugExpressionEvaluator.](../../extensibility/debugger/reference/idebugexpressionevaluator.md) Em seguida, o DE chama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para converter a expressão (em forma de texto) para uma expressão parsed, pronta para avaliação. Esta expressão analisado é representada pela interface [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md) A expressão é tipicamente analisado e não avaliado neste momento.

 O DE cria um objeto que implementa a interface `IDebugParsedExpression` [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) coloca o objeto no `IDebugExpression2` objeto e retorna o `IDebugExpression2` objeto de `IDebugExpressionContext2::ParseText`.

### <a name="evaluate-the-expression"></a>Avalie a expressão
 O Visual Studio chama [o AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [o AssessAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para avaliar a expressão analisado. Ambos os métodos chamam`IDebugExpression2::EvaluateSync` [Descronia](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) (chama o método imediatamente, enquanto `IDebugExpression2::EvaluateAsync` chama o método através de um segmento de fundo) para avaliar a expressão analisado e retornar uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa o valor e o tipo da expressão analisado. `IDebugParsedExpression::EvaluateSync`usa o SH, endereço e binder fornecidos para converter a expressão `IDebugProperty2` analisado em um valor real, representado pela interface.

### <a name="for-example"></a>Por exemplo
 Depois que um ponto de ruptura é atingido em um programa em execução, o usuário escolhe exibir uma variável na caixa de diálogo **QuickWatch.** Esta caixa de diálogo mostra o nome da variável, seu valor e seu tipo. O usuário pode normalmente alterar o valor.

 Quando a caixa de diálogo **QuickWatch** é mostrada, o nome da variável que está sendo examinada é enviado como texto para [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md). Isso retorna um objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) representando a expressão analisado, neste caso, a variável. [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) é então chamado `IDebugProperty2` para produzir um objeto que representa o valor e o tipo da variável, bem como seu nome. É essa informação que é exibida.

 Se o usuário mudar o valor da variável, [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) é chamado com o novo valor, que altera o valor da variável na memória para que ela seja usada quando o programa for retomado.

 Consulte Exibindo locais para obter mais [detalhes](../../extensibility/debugger/displaying-locals.md) sobre esse processo de exibição dos valores das variáveis. Consulte [Alterar o valor de um local](../../extensibility/debugger/changing-the-value-of-a-local.md) para obter mais detalhes sobre como o valor de uma variável é alterado.

## <a name="in-this-section"></a>Nesta seção
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md) Fornece os argumentos que são passados quando o DE chama o EE.

 [Principais interfaces avaliadoras de expressão](../../extensibility/debugger/key-expression-evaluator-interfaces.md) Descreve as interfaces cruciais necessárias ao escrever um EE, juntamente com o contexto de avaliação.

## <a name="see-also"></a>Confira também
- [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
- [Exibindo locais](../../extensibility/debugger/displaying-locals.md)
- [Mudando o valor de um local](../../extensibility/debugger/changing-the-value-of-a-local.md)
