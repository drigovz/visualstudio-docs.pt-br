---
title: IDebugThread2::Suspend | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e45cee0acab5fb2b5165e28895ab9a7dcb3ed9c1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915464"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende um thread.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Suspend ( 
   DWORD *pdwSuspendCount
);
```

```csharp
HRESULT Suspend ( 
   out uint pdwSuspendCount
);
```

#### <a name="parameters"></a>Parâmetros
 `pdwSuspendCount`

 [out] Retorna a contagem de suspensão após a operação de suspensão.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cada chamada para esse método incrementa a contagem de suspensões acima de 0. A contagem de suspensões é exibida na **Threads** janela de depuração.

 Para cada chamada para esse método, deve haver uma chamada posterior para o [retomar](../../../extensibility/debugger/reference/idebugthread2-resume.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md)