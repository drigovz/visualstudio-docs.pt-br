---
title: 'IDebugThread2:: resume | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80718678"
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
fora Retorna a contagem de suspensão após a operação de retomada.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Cada chamada para esse método diminui a contagem de suspensões até chegar a 0 em que momento, a execução é realmente retomada. Essa contagem de suspensão é exibida na janela de depuração de **threads** .

 Para cada chamada para esse método, deve haver uma chamada anterior para o método [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . A contagem de suspensão determina quantas vezes o `IDebugThread2::Suspend` método foi chamado até o momento.

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)
