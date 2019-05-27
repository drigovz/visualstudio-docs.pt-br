---
title: IDebugFunctionObject::CreateStringObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateStringObject
helpviewer_keywords:
- IDebugFunctionObject::CreateStringObject method
ms.assetid: fd6070ab-07d4-4ea1-8d71-b16592d6f1a7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b8c5b166917960c00582ad1df41fe8e4a9088079
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66199120"
---
# <a name="idebugfunctionobjectcreatestringobject"></a>IDebugFunctionObject::CreateStringObject
Cria um objeto de cadeia de caracteres.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateStringObject( 
   LPCOLESTR      pcstrString,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObject(
   string      pcstrString,
   out IDebugObject ppOjbect
);
```

## <a name="parameters"></a>Parâmetros
`pcstrString`\
[in] O valor de cadeia de caracteres para o objeto de cadeia de caracteres.

`ppObject`\
[out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o objeto de cadeia de caracteres criada recentemente.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa uma cadeia de caracteres que é um parâmetro para a função que é representado pela [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.

## <a name="see-also"></a>Consulte também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)