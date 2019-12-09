---
title: IEnumDebugModules2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugModules2::Next
helpviewer_keywords:
- IEnumDebugModules2::Next
ms.assetid: 46b7ccad-b07b-4ec0-b3ce-13981ffab7e8
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5ce512cde85dd305b2d9efb360d805eddbba40e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350296"
---
# <a name="ienumdebugmodules2next"></a>IEnumDebugModules2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugModule2** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugModule2[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>Parâmetros
`celt`\
[in] O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.

`rgelt`\
[no, out] Matriz de [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) elementos a serem preenchidos.

`pceltFetched`\
[out] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)