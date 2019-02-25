---
title: IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreatePrimitiveObject
helpviewer_keywords:
- IDebugFunctionObject::CreatePrimitiveObject method
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 185466d8bb89b504d7b6f8df4b624390205d3944
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685281"
---
# <a name="idebugfunctionobjectcreateprimitiveobject"></a>IDebugFunctionObject::CreatePrimitiveObject
Cria um objeto de dados primitivos, como um inteiro simples.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreatePrimitiveObject( 
   OBJECT_TYPE    ot,
   IDebugObject** ppObject
);
```

```csharp
int CreatePrimitiveObject(
   enum_OBJECT_TYPE ot,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parâmetros
 `ot`

 [in] Um valor a partir de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeração que representa o tipo primitivo para criar.

 `ppObject`

 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto recém-criado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa um objeto primitivo que é um parâmetro para a função que é representado pela [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface. Por exemplo, se a cadeia de caracteres de expressão for "myString(5)", esse método seria usado para criar um objeto que representa o inteiro 5.

## <a name="see-also"></a>Consulte também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)