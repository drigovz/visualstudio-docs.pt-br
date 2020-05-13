---
title: IDebugObject::Equalequal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::IsEqual
helpviewer_keywords:
- IDebugObject::IsEqual method
ms.assetid: 4b76e663-ef2e-41ff-9be1-bf26d666a34a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13018e31fb5f8bed89a0a290d687360a605a855d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726508"
---
# <a name="idebugobjectisequal"></a>IDebugObject::IsEqual
Compara um objeto com este objeto.

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

## <a name="parameters"></a>parâmetros
`pObject`\
[em] Um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) representando o objeto para comparar.

`pfIsEqual`\
[fora] Retorna não-zero`TRUE`( ) se os valores dos objetos forem iguais; caso contrário, retorna`FALSE`zero ( ).

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, este método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e este objeto [IDebugObject;](../../../extensibility/debugger/reference/idebugobject.md) se os endereços são iguais, então os objetos podem ser considerados iguais.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
