---
title: IDebugCanStopEvent2::GetReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 59e611c3ed69528f92a6085cf74aa44efed09144
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734529"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Fica por isso que o motor de depuração (DE) quer parar.

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

## <a name="parameters"></a>parâmetros
`pcr`\
[fora] Retorna um valor da enumeração [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) que descreve o motivo deste evento.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é tipicamente chamado antes do método [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para que`TRUE`o chamador possa determinar se deve passar não-zero ( ) para o `IDebugCanStopEvent2::CanStop` método.

 A razão para parar `CANSTOP_ENTRYPOINT`pode ser, o que significa `CANSTOP_STEPIN`que o DE atingiu um ponto de entrada, ou , o que significa que o DE entrou em uma função.

## <a name="see-also"></a>Confira também
- [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)
- [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)
- [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)
