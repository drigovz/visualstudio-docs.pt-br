---
title: IDebugReference2::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetMemoryContext
helpviewer_keywords:
- IDebugReference2::GetMemoryContext
ms.assetid: 47fc3827-07a0-4eee-b7f4-fc1c62e6b25c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ec0c2b91162a88cfbc43525408fef2294ec32102
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66207927"
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

## <a name="parameters"></a>Parâmetros
`ppMemory`\
[out] Retorna o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que representa a memória associada com o valor da referência.

## <a name="return-value"></a>Valor de retorno
 Sempre retorna `E_NOTIMPL`.

## <a name="see-also"></a>Consulte também
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)