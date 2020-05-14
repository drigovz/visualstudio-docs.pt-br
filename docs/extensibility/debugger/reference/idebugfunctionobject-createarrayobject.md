---
title: IDebugFunctionObject::CreateArrayObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bd4c07f2b95ff3077de79d4bc63f4fad19b0c6fa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728609"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Cria um objeto de matriz. Esta matriz pode conter valores primitivos ou de instância de objeto.

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

## <a name="parameters"></a>parâmetros
`ot`\
[em] Especifica um valor da enumeração [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) indicando o tipo do novo objeto de matriz.

`pClassField`\
[em] Um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) representando a classe de um objeto, se criar uma matriz de valores de instância de objeto. Se criar uma matriz de objetos primitivos, este parâmetro é um valor nulo.

`dwRank`\
[em] A classificação ou número de dimensões da matriz.

`dwDims`\
[em] Os tamanhos de cada dimensão da matriz.

`dwLowBounds`\
[em] A origem de cada dimensão (tipicamente 0 ou 1).

`ppObject`\
[fora] Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando a matriz recém-criada. Este é, na verdade, um objeto [IDebugArrayObject.](../../../extensibility/debugger/reference/idebugarrayobject.md)

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame este método para criar um objeto que represente um parâmetro de matriz para a função que é representada pela interface [IDebugFunctionObject.](../../../extensibility/debugger/reference/idebugfunctionobject.md)

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
