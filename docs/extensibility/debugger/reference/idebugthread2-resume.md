---
title: IDebugThread2::Retomar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3899dea7c33946588de4308f42b948ede703361a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718678"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Retoma a execução de um fio.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Resume ( 
   DWORD *pdwSuspendCount
);
```

```csharp
int Resume ( 
   out uint pdwSuspendCount
);
```

## <a name="parameters"></a>parâmetros
`pdwSuspendCount`\
[fora] Retorna a contagem de suspensão após a operação de retomada.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cada chamada a este método diminui a contagem de suspensão até chegar a 0, momento em que, a execução é realmente retomada. Esta contagem de suspensão é exibida na janela de depuração **Threads.**

 Para cada chamada a este método, deve haver uma chamada prévia para o método [Suspender.](../../../extensibility/debugger/reference/idebugthread2-suspend.md) A contagem de suspensão `IDebugThread2::Suspend` determina quantas vezes o método foi chamado até agora.

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspender](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
