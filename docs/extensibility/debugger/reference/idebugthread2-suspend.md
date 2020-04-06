---
title: IDebugThread2::Suspenda | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a7dd5dc69effbd46986eff963de3e740d9aa8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718646"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
Suspende um fio.

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

## <a name="parameters"></a>parâmetros
`pdwSuspendCount`\
[fora] Retorna a contagem de suspensão após a operação de suspensão.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cada chamada para este método aumenta a contagem de suspensão acima de 0. Esta contagem de suspensão é exibida na janela de depuração **Threads.**

 Para cada chamada para este método, deve haver uma chamada posterior para o método [Retomar.](../../../extensibility/debugger/reference/idebugthread2-resume.md)

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Continuar](../../../extensibility/debugger/reference/idebugthread2-resume.md)
