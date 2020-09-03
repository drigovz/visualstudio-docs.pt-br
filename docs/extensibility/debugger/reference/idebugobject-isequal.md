---
title: 'IDebugObject:: IsEqual | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
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

## <a name="parameters"></a>Parâmetros
`pObject`\
no Um objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o objeto a ser comparado.

`pfIsEqual`\
fora Retornará um valor diferente de zero ( `TRUE` ) se os valores dos objetos forem iguais; caso contrário, retornará zero ( `FALSE` ).

## <a name="return-value"></a>Valor Retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Normalmente, esse método pode comparar os endereços dos valores representados pelo `pObject` parâmetro e esse objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) ; se os endereços forem iguais, os objetos poderão ser considerados iguais.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
