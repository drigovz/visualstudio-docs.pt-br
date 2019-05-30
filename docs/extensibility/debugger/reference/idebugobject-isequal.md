---
title: IDebugObject::IsEqual | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cf592fa83a18c47bf676b84073c0be0e4cb476e8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323581"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara um objeto com esse objeto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT IsEqual( 
   IDebugObject* pObject,
   BOOL*         pfIsEqual
);
```

```csharp
int IsEqual(
   IDebugObject pObject,
   out int      pfIsEqual
);
```

## <a name="parameters"></a>Parâmetros
`pObject`\
[in] Uma [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto que representa o objeto a ser comparado.

`pfIsEqual`\
[out] Retorna não zero (`TRUE`) se os valores dos objetos forem iguais; caso contrário, retornará zero (`FALSE`).

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto; se os endereços são iguais e, em seguida, os objetos podem ser considerados iguais.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)