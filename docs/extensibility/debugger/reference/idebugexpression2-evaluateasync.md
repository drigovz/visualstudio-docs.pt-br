---
title: IDebugExpression2::EvaluateAsync | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExpression2::EvaluateAsync
helpviewer_keywords:
- IDebugExpression2::EvaluateAsync
ms.assetid: 848fe6cb-0759-42f2-890b-d2b551c527d6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 55037d4a7dbc25cb422929020cf674eb41fbfe93
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66204136"
---
# <a name="idebugexpression2evaluateasync"></a>IDebugExpression2::EvaluateAsync
Esse método avalia a expressão de forma assíncrona.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT EvaluateAsync (
    EVALFLAGS             dwFlags,
    IDebugEventCallback2* pExprCallback
);
```

```csharp
int EvaluateAsync(
    enum_EVALFLAGS       dwFlags,
    IDebugEventCallback2 pExprCallback
);
```

## <a name="parameters"></a>Parâmetros
`dwFlags`\
[in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que controlam a avaliação da expressão.

`pExprCallback`\
[in] Esse parâmetro é sempre um valor nulo.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retornará um código de erro. Um código de erro típica é:

|Erro|Descrição|
|-----------|-----------------|
|E_EVALUATE_BUSY_WITH_EVALUATION|Outra expressão está sendo avaliada no momento, e não há suporte para a avaliação da expressão simultâneas.|

## <a name="remarks"></a>Comentários
Esse método deve retornar imediatamente depois de ter começado a avaliação da expressão. Quando a expressão é avaliada com êxito, uma [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) deve ser enviada para o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) retorno de chamada do evento conforme fornecido por meio de [anexar ](../../../extensibility/debugger/reference/idebugprogram2-attach.md) ou [anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md).

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um simples `CExpression` objeto que implementa o [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md) interface.

```cpp
HRESULT CExpression::EvaluateAsync(EVALFLAGS dwFlags,
                                   IDebugEventCallback2* pExprCallback)
{
    // Set the aborted state to FALSE
    // in case the user tries to redo the evaluation after aborting.
    m_bAborted = FALSE;
    // Post the WM_EVAL_EXPR message in the message queue of the current thread.
    // This starts the expression evaluation on a background thread.
    PostThreadMessage(GetCurrentThreadId(), WM_EVAL_EXPR, 0, (LPARAM) this);
    return S_OK;
}
```

## <a name="see-also"></a>Consulte também
- [IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)
- [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
