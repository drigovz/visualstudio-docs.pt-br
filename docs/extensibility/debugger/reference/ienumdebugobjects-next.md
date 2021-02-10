---
title: 'IEnumDebugObjects:: Next | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Next
helpviewer_keywords:
- IEnumDebugObjects::Next method
ms.assetid: e54c3055-6030-4dc9-9f7a-5e3ce75f252f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7ef009a4801e40859e2b757465bb15ffac97395a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957108"
---
# <a name="ienumdebugobjectsnext"></a>IEnumDebugObjects::Next
Esse método retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG          celt,
   IDebugObject** rgelt,
   ULONG*         pceltFetched
);
```

```csharp
int Next(
   uint           celt,
   IDebugObject[] rgelt,
   ref uint       pceltFetched
);
```

## <a name="parameters"></a>Parâmetros
`celt`\
no O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.

`rgelt`\
[entrada, saída] Matriz de elementos [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) a ser preenchida.

`pceltFetched`\
fora Retorna o número de elementos realmente retornados em `rgelt` .

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos puder ser retornado; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
