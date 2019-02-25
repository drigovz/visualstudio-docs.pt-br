---
title: IDebugBinder::Bind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::Bind
helpviewer_keywords:
- IDebugBinder::Bind method
ms.assetid: 15a11ad7-0fcc-4e80-ae34-8a7dd7bae3c3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcb3535a2ace5818664a34a5d7b818d7dfd8b025
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704937"
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

#### <a name="parameters"></a>Parâmetros
 `pContainer`

 [in] O [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que contém o filho referenciado por `pField`.

 `pField`

 [in] O [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa o símbolo.

 `ppObject`

 [out] Retorna o `IDebugObject` que representa a instância do símbolo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Consulte também
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)