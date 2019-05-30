---
title: IDebugThread2::GetThreadId | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::GetThreadId
helpviewer_keywords:
- IDebugThread2::GetThreadId
ms.assetid: db8b1c07-6b86-47f9-b292-bac19c276d36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 66ad2151f6455d758d57c51a387184a9fcce8ec7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320174"
---
# <a name="idebugthread2getthreadid"></a>IDebugThread2::GetThreadId
Obtém o identificador de thread do sistema.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetThreadId (
    DWORD* pdwThreadId
);
```

```csharp
int GetThreadId (
    out uint pdwThreadId
);
```

## <a name="parameters"></a>Parâmetros
`pdwThreadId`\
[out] Retorna o identificador de thread do sistema.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Uma ID de thread é usada para identificar um thread entre todos os outros threads em um processo.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um simples `CProgram` objeto que implementa o [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) interface.

```cpp
HRESULT CProgram::GetThreadId(DWORD* pdwThreadId) {
    *pdwThreadId = GetCurrentThreadId();
    return NOERROR;
}
```

## <a name="see-also"></a>Consulte também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
