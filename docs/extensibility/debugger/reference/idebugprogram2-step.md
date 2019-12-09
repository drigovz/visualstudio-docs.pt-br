---
title: IDebugProgram2::Step | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8030bd45850a2b81e3cfb03a83497bba77c4515c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66325290"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Executa uma etapa.

> [!NOTE]
> Este método foi preterido. Use o [etapa](../../../extensibility/debugger/reference/idebugprocess3-step.md) método em vez disso.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Step( 
   IDebugThread2*  pThread,
   STEPKIND        sk,
   STEPUNIT        step
);
```

```csharp
int Step( 
   IDebugThread2  pThread,
   enum_STEPKIND  sk,
   enum_STEPUNIT  step
);
```

## <a name="parameters"></a>Parâmetros
`pThread`\
[in] Uma [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) objeto que representa o thread que está sendo passado.

`sk`\
[in] Um valor a partir de [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) enumeração que especifica o tipo de etapa.

`step`\
[in] Um valor a partir de [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) enumeração que especifica a unidade de etapa (por exemplo, pela instrução ou instrução).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Caso haja qualquer sincronização de thread ou a comunicação entre threads, outros threads no programa devem ser executado quando um determinado thread passo a passo.

> [!WARNING]
> Não enviar um evento de interrupção ou um evento (síncrono) imediato [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ao manipular essa chamada; caso contrário, o depurador poderá parar de responder.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)