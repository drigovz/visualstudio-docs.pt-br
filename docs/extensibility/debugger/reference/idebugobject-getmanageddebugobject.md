---
title: IDebugObject::GetManagedDebugObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetManagedDebugObject
helpviewer_keywords:
- IDebugObject::GetManagedDebugObject method
ms.assetid: cb89692e-7657-47ff-846d-311943521951
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b0721e8f8a30a8736f6d52ea61e02b9a93821a98
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203006"
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

## <a name="parameters"></a>Parâmetros
`ppObject`\
[out] Retorna um [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto que representa o objeto gerenciado recém-criado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro. Retornará E_FAIL se este [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) não representa uma instância da classe de valor gerenciado.

## <a name="remarks"></a>Comentários
 Isso [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) objeto deve representar uma instância da classe de valor gerenciado, como um `System.Decimal` instância. Fazendo uma cópia local, a sobrecarga da chamada [Evaluate](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) é eliminado.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)