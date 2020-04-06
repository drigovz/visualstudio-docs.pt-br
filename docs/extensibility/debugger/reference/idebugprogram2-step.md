---
title: IDebugProgram2::Passo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 194e72eba5a3f137e4650752a090d91ad7c402fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722764"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Realiza um passo.

> [!NOTE]
> Esse método é preterido. Use o método [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) em vez disso.

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

## <a name="parameters"></a>parâmetros
`pThread`\
[em] Um objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento sendo pisado.

`sk`\
[em] Um valor da enumeração [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) que especifica o tipo de passo.

`step`\
[em] Um valor da enumeração [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) que especifica a unidade de etapa (por exemplo, por instrução ou instrução).

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 No caso de haver alguma sincronização de rosca ou comunicação entre segmentos, outros segmentos do programa devem ser executados quando um segmento específico estiver pisando.

> [!WARNING]
> Não envie um evento de parada ou um evento imediato (síncrono) para [o Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) durante o tratamento desta chamada; caso contrário, o depurador pode travar.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
