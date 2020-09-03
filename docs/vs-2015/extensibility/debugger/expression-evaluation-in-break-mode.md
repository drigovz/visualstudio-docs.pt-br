---
title: Avaliação de expressão no modo de interrupção | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 362e50e20519c358564d13ba169f706fe384ca5c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152755"
---
# <a name="expression-evaluation-in-break-mode"></a>Avaliação de expressão no modo de interrupção
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

O seguinte descreve o processo que ocorre quando o depurador está no modo de interrupção e deve realizar a avaliação da expressão.  
  
## <a name="expression-evaluation-process"></a>Processo de avaliação de expressão  
 Estas são as etapas básicas envolvidas na avaliação de uma expressão:  
  
1. O SDM (Gerenciador de depuração de sessão) chama [IDebugStackFrame2:: GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter uma interface de contexto de expressão, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).  
  
2. Em seguida, o SDM chama [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) com a cadeia de caracteres a ser analisada.  
  
3. Se ParseText não retornar S_OK, o motivo do erro será retornado.  
  
     ,  
  
     Se ParseText retornar S_OK, o SDM poderá chamar [IDebugExpression2:: EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter um valor final da expressão analisada.  
  
    - No caso do uso do `IDebugExpression2::EvaluateSync` , a interface de retorno de chamada fornecida é usada para comunicar o processo contínuo da avaliação. O valor final é retornado em uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) .  
  
    - No caso do uso do `IDebugExpression2::EvaluateAsync` , a interface de retorno de chamada fornecida é usada para comunicar o processo contínuo da avaliação. Depois que a avaliação for concluída, o EvaluateAsync enviará uma interface [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) por meio do retorno de chamada. Com essa interface de evento, o valor final pode ser obtido com [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)
