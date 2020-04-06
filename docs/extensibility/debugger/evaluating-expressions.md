---
title: Avaliando expressões | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18e342704cbb4abd7de9667576ce331ef8fbf60a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738832"
---
# <a name="evaluate-expressions"></a>Avaliar expressões
As expressões são criadas a partir de strings passadas a partir das janelas **Autos,** **Watch,** **QuickWatch**ou **Immediate.** Quando uma expressão é avaliada, ela gera uma seqüência imprimível que contém o nome e o tipo de variável ou argumento e seu valor. Esta seqüência é exibida na janela IDE correspondente.

## <a name="implementation"></a>Implementação
 As expressões são avaliadas quando um programa é interrompido em um ponto de ruptura. A expressão em si é representada por uma interface [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) que representa uma expressão parsed que está pronta para vinculação e avaliação dentro do contexto de avaliação de expressão dado. O quadro de pilha determina o contexto de avaliação de expressão, que o mecanismo de depuração (DE) fornece implementando a interface [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

 Dada uma seqüência de usuário e uma interface [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) um mecanismo de depuração (DE) pode obter uma interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) passando a string do usuário para o método [IDebugExpressionContext2::ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) A interface IDebugExpression2 retornada contém a expressão analisado pronta para avaliação.

 Com `IDebugExpression2` a interface, o DE pode obter o valor da expressão através de avaliação de expressão síncrona ou assíncrona, usando [IDebugExpression2::AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::AssessAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Este valor, juntamente com o nome e o tipo da variável ou argumento, é enviado ao IDE para exibição. O valor, nome e tipo são representados por uma interface [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

 Para habilitar a avaliação de expressão, um DE deve implementar as interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md) A avaliação síncrona e assíncrona exigem a implementação do método [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

## <a name="see-also"></a>Confira também
- [Quadros de pilha](../../extensibility/debugger/stack-frames.md)
- [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)
- [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
