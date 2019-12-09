---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e1b219973e0fced92a588a87ed472cf7a57d312d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66337268"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Obtém o motivo por que deseja interromper o mecanismo de depuração (DES).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetReason( 
   CANSTOP_REASON* pcr
);
```

```csharp
int GetReason( 
   out enum_CANSTOP_REASON pcr
);
```

## <a name="parameters"></a>Parâmetros
`pcr`\
[out] Retorna um valor da [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) enumeração que descreve o motivo para esse evento.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, esse método é chamado antes do [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) método para que o chamador possa determinar se deve passar diferente de zero (`TRUE`) para o `IDebugCanStopEvent2::CanStop` método.

 O motivo para interrupção pode ser `CANSTOP_ENTRYPOINT`, que significa que o DE atingiu um ponto de entrada, ou `CANSTOP_STEPIN`, que significa que o DE tiver entrado em uma função.

## <a name="see-also"></a>Consulte também
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)