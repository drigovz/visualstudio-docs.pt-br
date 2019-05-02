---
title: Avaliação da expressão no modo de interrupção | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a31bc56673ec9e82206a8829aaf89328eb9198d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925675"
---
# <a name="expression-evaluation-in-break-mode"></a>Avaliação da expressão no modo de interrupção
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de interrupção e deverá conduzir a avaliação da expressão.

## <a name="expression-evaluation-process"></a>Processo de avaliação de expressão
 A seguir estão as etapas básicas envolvidas na avaliação de uma expressão:

1. O Gerenciador de sessão de depuração (SDM) chama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter uma interface de contexto de expressão, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. Em seguida, chama o SDM [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) com a cadeia de caracteres a ser analisada.

3. Se ParseText não retornar S_OK, o motivo do erro é retornado.

     -otherwise-

     Se ParseText retornar S_OK, o SDM, em seguida, pode chamar o [IDebugExpression2::EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter um valor final da expressão analisada.

    - Ao usar `IDebugExpression2::EvaluateSync`, a interface de retorno de chamada fornecido se comunica o processo contínuo de avaliação. O valor final é retornado em uma [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) interface.

    - Ao usar `IDebugExpression2::EvaluateAsync`, a interface de retorno de chamada fornecido se comunica o processo contínuo de avaliação. Depois que a avaliação for concluída, EvaluateAsync envia um [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) interface por meio do retorno de chamada. Com essa interface de eventos, o valor final de resultados com [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Consulte também
- [Chamar eventos do depurador](../../extensibility/debugger/calling-debugger-events.md)