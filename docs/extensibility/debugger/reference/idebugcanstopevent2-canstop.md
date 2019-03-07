---
title: IDebugCanStopEvent2::CanStop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::CanStop
helpviewer_keywords:
- IDebugCanStopEvent2::CanStop
ms.assetid: 7d61adbe-6b3d-41f3-86a1-45d9cc01a7f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 307b6d25f2e45276ead7c4b360ae191a01059104
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56716552"
---
# <a name="idebugcanstopevent2canstop"></a>IDebugCanStopEvent2::CanStop
Notifica o mecanismo de depuração (DES) ou não interromper no local atual do código ou simplesmente continuar a execução.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CanStop ( 
   BOOL fCanStop
);
```

```csharp
int CanStop ( 
   int fCanStop
);
```

#### <a name="parameters"></a>Parâmetros
 `fCanStop`

 [in] Diferente de zero (`TRUE`) se o DE deve parar no local atual do código; caso contrário, zero (`FALSE`).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O receptor desse evento normalmente chama o [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md) método para determinar o motivo pelo qual o DE que deseja interromper e, em seguida, chama o `IDebugCanStopEvent2::CanStop` método com a resposta apropriada.

 Se o DE parar, ele envia um evento que descreve o motivo para interrupção. Normalmente, há dois eventos que são enviadas, uma quebra de usuário ou sinal representada pela [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) interface e um evento de ponto de interrupção representado pela [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) interface.

## <a name="see-also"></a>Consulte também
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
- [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)
- [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)