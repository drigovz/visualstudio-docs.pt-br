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
ms.openlocfilehash: 53c1961eb1ed72580fc314d7a1542ddc926780f9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205817"
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