---
title: IDebugEngineProgram2::WatchForThreadStep | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineProgram2::WatchForThreadStep
helpviewer_keywords:
- IDebugEngineProgram2::WatchForThreadStep
ms.assetid: b70922a3-1313-409a-b3b7-50c7cd13e394
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5381cff406e3b6e182a6ecbb191381061fb3758
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920384"
---
# <a name="idebugengineprogram2watchforthreadstep"></a>IDebugEngineProgram2::WatchForThreadStep
Aguarda a execução (ou interrompe a assistir a execução) para ocorrer em determinado thread.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WatchForThreadStep( 
   IDebugProgram2* pOriginatingProgram,
   DWORD           dwTid,
   BOOL            fWatch,
   DWORD           dwFrame
);
```

```csharp
int WatchForThreadStep( 
   IDebugProgram2 pOriginatingProgram,
   uint           dwTid,
   int            fWatch,
   uint           dwFrame
);
```

#### <a name="parameters"></a>Parâmetros
 `pOriginatingProgram`

 [in] Uma [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) objeto que representa o programa que está sendo passado.

 `dwTid`

 [in] Especifica o identificador do thread para assistir.

 `fWatch`

 [in] Diferente de zero (`TRUE`) significa começar a observar para execução no thread identificado por `dwTid`; caso contrário, zero (`FALSE`) significa parar de monitorar para execução em `dwTid`.

 `dwFrame`

 [in] Especifica um índice do quadro que controla o tipo de etapa. Quando se trata do que valor é zero (0), o tipo de etapa é "step into" e o programa deve ser interrompida sempre que o thread identificado por `dwTid` executa. Quando `dwFrame` é diferente de zero, o tipo de etapa é "step over" e o programa deve parar somente se o thread identificado por `dwTid` está em execução em um quadro cujo índice é igual ou superior na pilha que `dwFrame`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Quando o Gerenciador de sessão de depuração (SDM) as etapas de um programa, identificado pelo `pOriginatingProgram` parâmetro, ele notifica todos os outros programas conectados ao chamar esse método.

 Esse método é aplicável somente a revisão do mesmo thread.

## <a name="see-also"></a>Consulte também
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)