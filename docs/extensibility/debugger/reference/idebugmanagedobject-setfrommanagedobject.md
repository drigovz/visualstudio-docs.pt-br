---
title: IDebugManagedObject::SetFromManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::SetFromManagedObject
helpviewer_keywords:
- IDebugManagedObject::SetFromManagedObject method
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c56ccea9847cc23e45f9877f3d331be723293ee7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56712184"
---
# <a name="idebugmanagedobjectsetfrommanagedobject"></a>IDebugManagedObject::SetFromManagedObject
Define o valor da instância do objeto de classe de valor da instância da classe de valor fornecida como um parâmetro.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetFromManagedObject( 
   IUnknown* pManagedObject
);
```

```csharp
int SetFromManagedObject(
   object pManagedObject
);
```

#### <a name="parameters"></a>Parâmetros
 `pManagedObject`

 [in] Uma interface que representa o objeto gerenciado que contém o novo valor.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é usado para alterar o objeto gerenciado, conforme representado pela [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) objeto.

## <a name="see-also"></a>Consulte também
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)