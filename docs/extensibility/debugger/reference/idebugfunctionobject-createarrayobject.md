---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7ee5d4a59442238b461361522b06087650547b3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56685138"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Cria um objeto de matriz. Esta matriz pode conter qualquer um dos primitivos ou valores de instância do objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreateArrayObject( 
   OBJECT_TYPE    ot,
   IDebugField*   pClassField,
   DWORD          dwRank,
   DWORD          dwDims[],
   DWORD          dwLowBounds[],
   IDebugObject** ppObject
);
```

```csharp
int CreateArrayObject(
   enum_OBJECT_TYPE ot,
   IDebugField      pClassField,
   uint             dwRank,
   uint[]           dwDims,
   uint[]           dwLowBounds,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parâmetros
 `ot`

 [in] Especifica um valor a partir de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) enumeração que indica o tipo do novo objeto de matriz.

 `pClassField`

 [in] Uma [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto que representa a classe de um objeto, se os valores de instância de criação de uma matriz de objetos. Se criar uma matriz de objetos primitivos, este parâmetro é um valor nulo.

 `dwRank`

 [in] A classificação ou o número de dimensões da matriz.

 `dwDims`

 [in] Os tamanhos de cada dimensão da matriz.

 `dwLowBounds`

 [in] A origem de cada dimensão (geralmente 0 ou 1).

 `ppObject`

 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa a matriz criada recentemente. Isso é, na verdade, uma [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa um parâmetro de matriz para a função que é representada pela [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) interface.

## <a name="see-also"></a>Consulte também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)