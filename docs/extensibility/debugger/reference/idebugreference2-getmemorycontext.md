---
title: IDebugReference2::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7f7f49262c0efe9f856ba01a73382541067335f0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720596"
---
# <a name="idebugreference2getmemorycontext"></a>IDebugReference2::GetMemoryContext
Obtém um contexto de memória de uma referência. Reservado para uso futuro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext ( 
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>parâmetros
`ppMemory`\
[fora] Retorna o objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que representa a memória associada ao valor da referência.

## <a name="return-value"></a>Valor retornado
 Retorna sempre `E_NOTIMPL`.

## <a name="see-also"></a>Confira também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
