---
title: IDebugThread2::Resume | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5fc7b8f5cf5cd5360a60e8c6fbf3b6bf43415575
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65225993"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
Retoma a execução de um thread.

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

## <a name="parameters"></a>Parâmetros
 `pdwSuspendCount`\

 [out] Retorna a contagem de suspensão após a operação de retomada.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cada chamada para diminui esse método de contagem de suspensões até alcançar 0 nesse momento, a execução, na verdade, é retomada. A contagem de suspensões é exibida na **Threads** janela de depuração.

 Para cada chamada para esse método, deve haver uma chamada anterior para o [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) método. A contagem de suspensões determina quantas vezes o `IDebugThread2::Suspend` método foi chamado até o momento.

## <a name="see-also"></a>Consulte também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)