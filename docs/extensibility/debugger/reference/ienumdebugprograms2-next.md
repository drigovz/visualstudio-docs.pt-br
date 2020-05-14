---
title: IEnumDebugPrograms2::Próximo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Next
helpviewer_keywords:
- IEnumDebugPrograms2::Next
ms.assetid: 9120e263-e97c-4a40-ab2c-e9264ce3d6c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 035af638b9504318a39e01f34ed32719d957896e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715627"
---
# <a name="ienumdebugprograms2next"></a>IEnumDebugPrograms2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG            celt,
   IDebugProgram2** rgelt,
   ULONG*           pceltFetched
);
```

```csharp
int Next(
   uint             celt,
   IDebugProgram2[] rgelt,
   ref uint         pceltFetched
);
```

## <a name="parameters"></a>parâmetros
`celt`\
[em] O número de elementos para recuperar. Também especifica o tamanho `rgelt` máximo da matriz.

`rgelt`\
[dentro, fora] Matriz de elementos [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) a serem preenchidos.

`pceltFetched`\
[fora] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retornos `S_FALSE` se menos do que o número solicitado de elementos pode ser devolvido; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
