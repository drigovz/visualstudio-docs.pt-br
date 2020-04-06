---
title: IEnumDebugPropertyInfo2::Próximo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPropertyInfo2::Next
helpviewer_keywords:
- IEnumDebugPropertyInfo2::Next
ms.assetid: 4eb8c7c3-aadf-4187-abee-c0620308a3eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8e714f281835adf7df8d7e96a910ca66f1949b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80715518"
---
# <a name="ienumdebugpropertyinfo2next"></a>IEnumDebugPropertyInfo2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG                 celt,
   DEBUG_PROPERTY_INFO** rgelt,
   ULONG*                pceltFetched
);
```

```csharp
int Next(
   uint                  celt,
   DEBUG_PROPERTY_INFO[] rgelt,
   ref uint              pceltFetched
);
```

## <a name="parameters"></a>parâmetros
`celt`\
[em] O número de elementos para recuperar. Também especifica o tamanho `rgelt` máximo da matriz.

`rgelt`\
[dentro, fora] Matriz de elementos [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) a serem preenchidos.

`pceltFetched`\
[fora] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retornos `S_FALSE` se menos do que o número solicitado de elementos pode ser devolvido; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
