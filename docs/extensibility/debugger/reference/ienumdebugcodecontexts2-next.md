---
title: IEnumDebugCodeContexts2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::Next
helpviewer_keywords:
- IEnumDebugCodeContexts2::Next
ms.assetid: 0d8aa2db-0994-4166-b364-2e25d936fffc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c6e54b44d9e0ece42b65bf12412d6906158bc7fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717296"
---
# <a name="ienumdebugcodecontexts2next"></a>IEnumDebugCodeContexts2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG                celt,
   IDebugCodeContext2** rgelt,
   ULONG*               pceltFetched
);
```

```csharp
int Next(
   uint                 celt,
   IDebugCodeContext2[] rgelt,
   ref uint             pceltFetched
);
```

## <a name="parameters"></a>parâmetros
`celt`\
[em] O número de elementos para recuperar. Também especifica o tamanho `rgelt` máximo da matriz.

`rgelt`\
[dentro, fora] Matriz de elementos [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) a serem preenchidos.

`pceltFetched`\
[fora] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retornos `S_FALSE` se menos do que o número solicitado de elementos pode ser devolvido; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
