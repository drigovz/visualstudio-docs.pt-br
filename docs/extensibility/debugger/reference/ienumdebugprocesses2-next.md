---
title: IEnumDebugProcesses2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugProcesses2::Next
helpviewer_keywords:
- IEnumDebugProcesses2::Next
ms.assetid: abef89eb-198b-49cd-a4c9-17bce6cac0e1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0a35ad62d518bf9f19655809a8c1ac924da92bb8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62866241"
---
# <a name="ienumdebugprocesses2next"></a>IEnumDebugProcesses2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProcess2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProcess2[] rgelt,
   ref uint         pceltFetched
);
```

#### <a name="parameters"></a>Parâmetros
 `celt`

 [in] O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.

 `rgelt`

 [no, out] Matriz de [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) elementos a serem preenchidos.

 `pceltFetched`

 [out] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)