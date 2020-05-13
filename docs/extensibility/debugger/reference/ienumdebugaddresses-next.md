---
title: IEnumDebugEndereços::Próximo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugAddresses::Next
helpviewer_keywords:
- IEnumDebugAddresses::Next method
ms.assetid: 941e4be7-858d-433a-9259-18d0d017be9e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88deefddc5b479d7173c4de1c574c4da92631e97
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717641"
---
# <a name="ienumdebugaddressesnext"></a>IEnumDebugAddresses::Next
Este método retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG           celt,
   IDebugAddress** rgelt,
   ULONG*          pceltFetched
);
```

```csharp
int Next(
   uint            celt,
   IDebugAddress[] rgelt,
   ref uint        pceltFetched
);
```

## <a name="parameters"></a>parâmetros
`celt`\
[em] O número de elementos para recuperar. Também especifica o tamanho `rgelt` máximo da matriz.

`rgelt`\
[dentro, fora] Matriz de elementos [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) a serem preenchidos.

`pceltFetched`\
[fora] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retornos `S_FALSE` se menos do que o número solicitado de elementos pode ser devolvido; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
- [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)
