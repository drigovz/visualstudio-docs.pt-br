---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67d0d7a8642c9dd90067b0e197f420d4cc821faa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726681"
---
# <a name="idebugobjectgetmanageddebugobject"></a>IDebugObject::GetManagedDebugObject
Cria uma cópia do objeto gerenciado no espaço de endereço do mecanismo de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetManagedDebugObject( 
   IDebugManagedObject** ppObject
);
```

```csharp
int GetManagedDebugObject(
   out IDebugManagedObject ppObject
);
```

## <a name="parameters"></a>parâmetros
`ppObject`\
[fora] Retorna um objeto [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) representando o objeto gerenciado recém-criado.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro. Retorna E_FAIL se este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) não representar uma instância de classe de valor gerenciado.

## <a name="remarks"></a>Comentários
 Este objeto [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) deve representar uma instância de `System.Decimal` classe de valor gerenciada, como uma instância. Por ter uma cópia local, a sobrecarga de chamada [Avaliar](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) é eliminada.

## <a name="see-also"></a>Confira também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
