---
title: 'IDebugFunctionObject:: createarrayobject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::CreateArrayObject
helpviewer_keywords:
- IDebugFunctionObject::CreateArrayObject method
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 44d60c2f0573bf60d827737b2a54ff16b49d610c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929993"
---
# <a name="idebugfunctionobjectcreatearrayobject"></a>IDebugFunctionObject::CreateArrayObject
Cria um objeto de matriz. Essa matriz pode conter valores primitivos ou de instância de objeto.

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

## <a name="parameters"></a>Parâmetros
`ot`\
no Especifica um valor da enumeração de [OBJECT_TYPE](../../../extensibility/debugger/reference/object-type.md) indicando o tipo do novo objeto de matriz.

`pClassField`\
no Um objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) que representa a classe de um objeto, se estiver criando uma matriz de valores de instância de objeto. Se estiver criando uma matriz de objetos primitivos, esse parâmetro será um valor nulo.

`dwRank`\
no A classificação ou o número de dimensões da matriz.

`dwDims`\
no Os tamanhos de cada dimensão da matriz.

`dwLowBounds`\
no A origem de cada dimensão (normalmente 0 ou 1).

`ppObject`\
fora Retorna um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa a matriz recém-criada. Isso é, na verdade, um objeto [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) .

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Chame esse método para criar um objeto que representa um parâmetro de matriz para a função que é representada pela interface [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Confira também
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
