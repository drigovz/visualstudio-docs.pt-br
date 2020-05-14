---
title: Avaliando uma expressão da janela do relógio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Watch window expressions
- Watch window, expressions
- expression evaluation, Watch window expressions
ms.assetid: b07e72c7-60d3-4b30-8e3f-6db83454c348
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9cef2f27eec095ee7b136153ecb764feba9effbb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738845"
---
# <a name="evaluate-a-watch-window-expression"></a>Avalie a expressão da janela do relógio
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Quando a execução é pausada, o Visual Studio chama o mecanismo de depuração (DE) para determinar o valor atual de cada expressão em sua lista de observação. O DE avalia cada expressão usando um avaliador de expressão (EE), e o Visual Studio exibe seu valor na janela **relógio.**

 A seguir está uma visão geral de como uma expressão da lista de observação é avaliada:

1. O Visual Studio chama o [GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) do DE para obter um contexto de expressão que pode ser usado para avaliar expressões.

2. Para cada expressão na lista de observação, o Visual Studio chama [o ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) para converter o texto de expressão em uma expressão analisado.

3. `IDebugExpressionContext2::ParseText`chama [Parse](../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) para fazer o trabalho real de analisar o texto e produzir um objeto [IDebugParsedExpression.](../../extensibility/debugger/reference/idebugparsedexpression.md)

4. `IDebugExpressionContext2::ParseText`cria um objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e coloca o `IDebugParsedExpression` objeto nele. Este`DebugExpression2` objeto I é então devolvido ao Visual Studio.

5. O Visual Studio chama [o AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para avaliar a expressão analisado.

6. `IDebugExpression2::EvaluateSync`passa a chamada para [AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) para fazer a avaliação real e produzir um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que é devolvido ao Visual Studio.

7. O Visual Studio chama [o GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) para obter o valor da expressão que é exibida na lista de observação.

## <a name="parse-then-evaluate"></a>Parse então avaliar
 Uma vez que analisar uma expressão complexa pode levar muito mais tempo do que avaliá-la, o processo de avaliação de uma expressão é dividido em duas etapas: 1) analisar a expressão e 2) avaliar a expressão parsed. Dessa forma, a avaliação pode ocorrer muitas vezes, mas a expressão precisa ser analisada apenas uma vez. A expressão mediana do analisado é devolvida do EE em um objeto [IDebugParsedExpression](../../extensibility/debugger/reference/idebugparsedexpression.md) que, por sua vez, é encapsulado e retornado do DE como um objeto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md) O `IDebugExpression` objeto adia toda `IDebugParsedExpression` a avaliação para o objeto.

> [!NOTE]
> Não é necessário que um EE adere a esse processo de duas etapas, embora o Visual Studio assuma isso; o EE pode analisar e avaliar na mesma etapa quando [o AssessSync](../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md) é chamado (é assim que a amostra MyCEE funciona, por exemplo). Se o seu idioma pode formar expressões complexas, você pode querer separar o passo de análise da etapa de avaliação. Isso pode aumentar o desempenho no depurador do Visual Studio quando muitas expressões de relógio estão sendo mostradas.

## <a name="in-this-section"></a>Nesta seção
 [Implementação amostral da avaliação de expressão](../../extensibility/debugger/sample-implementation-of-expression-evaluation.md) Utiliza a amostra MyCEE para passar pelo processo de avaliação de expressão.

 [Avaliando uma expressão de relógio](../../extensibility/debugger/evaluating-a-watch-expression.md) Explica o que acontece depois de uma análise de expressão bem sucedida.

## <a name="related-sections"></a>Seções relacionadas
 [Contexto de avaliação](../../extensibility/debugger/evaluation-context.md) Fornece os argumentos que são passados quando o mecanismo de depuração (DE) chama o avaliador de expressão (EE).

## <a name="see-also"></a>Confira também
 [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
