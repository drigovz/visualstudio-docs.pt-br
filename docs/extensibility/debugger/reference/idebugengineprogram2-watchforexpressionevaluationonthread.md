---
title: idebugEngineProgram2::WatchForExpressionEvaluationOnThread | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
helpviewer_keywords:
- IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
ms.assetid: 01d05e77-8cac-4d1b-b19f-25756767ed27
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e988e1d64af38a55f5d946f704e1edb4df29b1d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730369"
---
# <a name="idebugengineprogram2watchforexpressionevaluationonthread"></a>IDebugEngineProgram2::WatchForExpressionEvaluationOnThread
Permite (ou não permite) que a avaliação de expressão ocorra no segmento dado, mesmo que o programa tenha parado.

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

## <a name="parameters"></a>parâmetros
`pOriginatingProgram`\
[em] Um objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) representando o programa que está avaliando uma expressão.

`dwTid`\
[em] Especifica o identificador do segmento.

`dwEvalFlags`\
[em] Uma combinação de bandeiras da [enumeração EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) que especifica como a avaliação deve ser realizada.

`pExprCallback`\
[em] Um objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) a ser usado para enviar eventos de depuração que ocorrem durante a avaliação de expressão.

`fWatch`\
[em] Se não zero`TRUE`(), permite a avaliação `dwTid`de expressão no segmento identificado por ; caso contrário,`FALSE`zero ( ) não permite avaliação de expressão sobre esse segmento.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Quando o gerenciador de depuração de sessão (SDM) pede a um programa, identificado pelo `pOriginatingProgram` parâmetro, para avaliar uma expressão, ele notifica todos os outros programas anexados chamando esse método.

 A avaliação de expressão em um programa pode fazer com que `IDispatch` o código seja executado em outro, devido à avaliação da função ou avaliação de quaisquer propriedades. Por causa disso, este método permite que a avaliação de expressão seja executada e concluída, mesmo que o segmento possa ser interrompido neste programa.

## <a name="see-also"></a>Confira também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
