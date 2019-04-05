---
title: Avaliação de expressões | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK], evaluating
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5ccfcc80-dea5-48a1-8bae-6a26f8d3bc56
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caff42c2e203151c6bab7d50b41744c2469ab3c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58921790"
---
# <a name="evaluating-expressions"></a>Avaliando expressões
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As expressões são criadas de cadeias de caracteres passadas do Autos, inspeção, QuickWatch ou windows imediatas. Quando uma expressão é avaliada, ele gera uma cadeia de caracteres imprimível que contém o nome e tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela do IDE correspondente.  
  
## <a name="implementation"></a>Implementação  
 Expressões são avaliadas quando um programa foi interrompido no ponto de interrupção. A expressão em si é representada por um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, que representa uma expressão analisada que está pronta para vinculação e avaliação dentro do contexto de avaliação de expressão fornecida. O quadro de pilhas determina o contexto de avaliação de expressão, que o mecanismo de depuração (DES) fornece ao implementar o [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
 Dada uma cadeia de caracteres de usuário e uma [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface, um mecanismo de depuração (DES) pode obter uma [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interface, passando a cadeia de caracteres do usuário para o [ IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método. A interface de IDebugExpression2 retornada contém a expressão analisada pronta para avaliação.  
  
 Com o `IDebugExpression2` interface, a Alemanha pode obter o valor da expressão por meio da avaliação de expressão síncrona ou assíncrona, usando [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado para o IDE para exibição. O valor, nome e tipo são representados por uma [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.  
  
 Para habilitar a avaliação da expressão, a DE deve implementar o [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interfaces. Avaliação síncrona e assíncrona exigir a implementação do [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) método.  
  
## <a name="see-also"></a>Consulte também  
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Contexto de avaliação de expressão](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
