---
title: Avaliação de expressão no modo break | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, expression evaluation
- debugging [Debugging SDK], expression evaluation
- expression evaluation, break mode
ms.assetid: 34fe5b58-15d5-4387-a266-72120f90a4b6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc09fc43bd9f0edea4f6dc32e5f37c387c045796
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738727"
---
# <a name="expression-evaluation-in-break-mode"></a>Avaliação de expressão no modo de quebra
A seção a seguir descreve o processo que ocorre quando o depurador está no modo de quebra e deve realizar a avaliação de expressão.

## <a name="expression-evaluation-process"></a>Processo de avaliação de expressão
 A seguir estão as etapas básicas envolvidas na avaliação de uma expressão:

1. O SDM (Session Debug Manager, gerenciador de depuração de sessão) chama [IDebugStackFrame2::GetExpressionContext](../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md) para obter uma interface de contexto de expressão, [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md).

2. O SDM então chama [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) com a seqüência de string a ser analisado.

3. Se o ParseText não retornar S_OK, o motivo do erro será devolvido.

     - caso contrário...

     Se o ParseText retornar S_OK, o SDM poderá então chamar [IDebugExpression2::AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou [IDebugExpression2::AssessAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter um valor final da expressão analisado.

    - Ao `IDebugExpression2::EvaluateSync`usar, a interface de retorno de chamada dada comunica o processo contínuo da avaliação. O valor final é devolvido em uma interface [IDebugProperty2.](../../extensibility/debugger/reference/idebugproperty2.md)

    - Ao `IDebugExpression2::EvaluateAsync`usar, a interface de retorno de chamada dada comunica o processo contínuo da avaliação. Uma vez concluída a avaliação, o AssessAsync envia uma interface [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) através do retorno de chamada. Com esta interface de evento, o valor final resulta com [GetResult](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md).

## <a name="see-also"></a>Confira também
- [Eventos de depurador de chamadas](../../extensibility/debugger/calling-debugger-events.md)
