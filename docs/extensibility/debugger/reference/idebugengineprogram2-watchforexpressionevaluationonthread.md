---
title: IDebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e72292f403b28c66cddbcee623f27ddfcbe5c3aa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345172"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permite (ou não) a avaliação da expressão para ocorrer em determinado thread, mesmo se o programa foi interrompido.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WatchForExpressionEvaluationOnThread( 
   IDebugProgram2*       pOriginatingProgram,
   DWORD                 dwTid,
   DWORD                 dwEvalFlags,
   IDebugEventCallback2* pExprCallback,
   BOOL                  fWatch
);
```

```csharp
int WatchForExpressionEvaluationOnThread( 
   IDebugProgram2       pOriginatingProgram,
   uint                  dwTid,
   uint                  dwEvalFlags,
   IDebugEventCallback2 pExprCallback,
   int                   fWatch
);
```

## <a name="parameters"></a>Parâmetros
`pOriginatingProgram`\
[in] Uma [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa que está avaliando uma expressão.

`dwTid`\
[in] Especifica o identificador do thread.

`dwEvalFlags`\
[in] Uma combinação de sinalizadores do [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) enumeração que especificam como a avaliação deve ser executada.

`pExprCallback`\
[in] Uma [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto a ser usado para enviar eventos de depuração que ocorrem durante a avaliação da expressão.

`fWatch`\
[in] Se diferente de zero (`TRUE`), permite que a avaliação da expressão no thread identificado por `dwTid`; caso contrário, zero (`FALSE`) não permite a avaliação da expressão naquele thread.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Quando o Gerenciador de sessão de depuração (SDM) solicita um programa, identificado pelo `pOriginatingProgram` parâmetro, a fim de avaliar uma expressão, ele notifica todos os outros programas conectados ao chamar esse método.

 Avaliação da expressão em um programa pode fazer com que o código seja executado em outro, devido a avaliação da função ou avaliação de qualquer `IDispatch` propriedades. Por isso, esse método permite que a avaliação da expressão ser executados e concluídos, mesmo que o thread pode ter sido interrompido neste programa.

## <a name="see-also"></a>Consulte também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)