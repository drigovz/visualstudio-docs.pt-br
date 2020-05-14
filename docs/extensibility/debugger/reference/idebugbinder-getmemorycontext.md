---
title: IDebugBinder::GetMemoryContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetMemoryContext
helpviewer_keywords:
- IDebugBinder::GetMemoryContext method
ms.assetid: 801c5b60-acff-4822-b23d-e9c7bbca8a0f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8d50126e26b836f7b53ee1abeb5c4988b74a2eed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735999"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Este método converte um local de objeto ou um endereço de memória em um contexto de memória.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMemoryContext( 
   IDebugField*           pField,
   DWORD                  dwConstant,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int GetMemoryContext(
   IDebugField              pField,
   uint                     dwConstant,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>parâmetros
`pField`\
[em] Um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) descrevendo o objeto para localizar. Se `NULL`, `dwConstant` em seguida, use em vez disso.

`dwConstant`\
[em] Um endereço de memória constante, como 0x5000.

`ppMemCxt`\
[fora] Retorna a interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que representa o endereço do objeto ou o endereço na memória.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
