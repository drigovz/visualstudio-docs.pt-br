---
title: Avaliando expressões | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151627"
---
# <a name="evaluating-expressions"></a>Avaliando expressões
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

As expressões são criadas a partir de cadeias de caracteres passadas das janelas automáticos, de inspeção, QuickWatch ou imediatas. Quando uma expressão é avaliada, ela gera uma cadeia de caracteres imprimível que contém o nome e o tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida na janela do IDE correspondente.  
  
## <a name="implementation"></a>Implementação  
 As expressões são avaliadas quando um programa é interrompido em um ponto de interrupção. A própria expressão é representada por uma interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , que representa uma expressão analisada que está pronta para associação e avaliação dentro do contexto de avaliação de expressão fornecido. O registro de ativação determina o contexto de avaliação da expressão, que o mecanismo de depuração (DE) fornece implementando a interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
 Dada uma cadeia de caracteres de usuário e uma interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , um mecanismo de depuração (de) pode obter uma interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) passando a cadeia de caracteres do usuário para o método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . A interface IDebugExpression2 retornada contém a expressão analisada pronta para avaliação.  
  
 Com a `IDebugExpression2` interface, o de pode obter o valor da expressão por meio de avaliação de expressão assíncrona ou síncrona, usando [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado para o IDE para exibição. O valor, o nome e o tipo são representados por uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
 Para habilitar a avaliação de expressão, um DE deve implementar as interfaces [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) e [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) . A avaliação síncrona e assíncrona requer a implementação do método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) .  
  
## <a name="see-also"></a>Consulte Também  
 [Quadros de pilha](../../extensibility/debugger/stack-frames.md)   
 [Contexto de avaliação da expressão](../../extensibility/debugger/expression-evaluation-context.md)   
 [Tarefas de depuração](../../extensibility/debugger/debugging-tasks.md)
