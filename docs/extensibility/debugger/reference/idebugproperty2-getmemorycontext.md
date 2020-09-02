---
title: 'IDebugProperty2:: GetMemoryContext | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetMemoryContext
helpviewer_keywords:
- IDebugProperty2::GetMemoryContext
ms.assetid: 91793d25-790f-4881-a5c0-d0458e534514
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8fa610af3ae00d30462c1a3a0c825e5a85722cdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80721464"
---
# <a name="idebugproperty2getmemorycontext"></a>IDebugProperty2::GetMemoryContext
Obtém o contexto de memória do valor da propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMemoryContext ( 
   IDebugMemoryContext2** ppMemory
);
```

```csharp
int GetMemoryContext(
   out IDebugMemoryContext2 ppMemory
);
```

## <a name="parameters"></a>Parâmetros
`ppMemory`\
fora Retorna o objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que representa a memória associada a essa propriedade.

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retorna `S_OK` ; caso contrário, retorna o código de erro. Retorna `S_GETMEMORYCONTEXT_NO_MEMORY_CONTEXT` se não houver nenhum contexto de memória para recuperar.

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
