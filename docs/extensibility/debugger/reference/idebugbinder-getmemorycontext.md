---
title: 'IDebugBinder:: GetMemoryContext | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735999"
---
# <a name="idebugbindergetmemorycontext"></a>IDebugBinder::GetMemoryContext
Esse método converte um local de objeto ou um endereço de memória em um contexto de memória.

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

## <a name="parameters"></a>Parâmetros
`pField`\
no Um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que descreve o objeto a ser localizado. Se `NULL` , em `dwConstant` vez disso, use.

`dwConstant`\
no Um endereço de memória constante, como 0x5000.

`ppMemCxt`\
fora Retorna a interface [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que representa o endereço do objeto ou o endereço na memória.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
