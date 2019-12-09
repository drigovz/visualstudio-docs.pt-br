---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 00d7e63b8a521ee25d2c7d378aeb82d064358ec9
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66344499"
---
# <a name="idebugbinderbind"></a>IDebugBinder::Bind
Esse método obtém o contexto de memória ou um objeto que contém o valor atual do símbolo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Bind( 
   IDebugObject*  pContainer,
   IDebugField*   pField,
   IDebugObject** ppObject
);
```

```csharp
int Bind(
   IDebugObject     pContainer,
   IDebugField      pField,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parâmetros
`pContainer`\
[in] O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que contém o filho referenciado por `pField`.

`pField`\
[in] O [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa o símbolo.

`ppObject`\
[out] Retorna o `IDebugObject` que representa a instância do símbolo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)