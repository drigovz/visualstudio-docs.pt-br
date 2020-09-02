---
title: 'IDebugBinder3:: getmemoryobject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetMemoryObject
helpviewer_keywords:
- IDebugBinder3::GetMemoryObject method
ms.assetid: 71d959c7-45df-485f-b0ee-f1c0439d54fb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 154873006091a213e69653d3742b3caa8c25b7e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735723"
---
# <a name="idebugbinder3getmemoryobject"></a>IDebugBinder3::GetMemoryObject
Esse método recupera um objeto de memória que representa a memória à qual esse objeto está associado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetMemoryObject(
   IDebugField*   pField,
   UINT64         uConstant,
   IDebugObject** ppObject
);
```

```csharp
int GetMemoryObject(
   IDebugField      pField,
   long             uConstant,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parâmetros
`pField`\
no Especifica para qual campo obter o objeto de memória.

`uConstant`\
no Representa um endereço de memória ou um valor para um valor constante.

`ppObject`\
fora Um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa a memória à qual esse objeto está associado.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
