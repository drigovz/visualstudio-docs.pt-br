---
title: IDebugManagedObject::GetManagedObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugManagedObject::GetManagedObject
helpviewer_keywords:
- IDebugManagedObject::GetManagedObject method
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a02fbe5b954fca78e2f75f982a62a1b9bf5f4a0b
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66210610"
---
# <a name="idebugmanagedobjectgetmanagedobject"></a>IDebugManagedObject::GetManagedObject
Retorna uma interface que representa o objeto gerenciado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetManagedObject( 
   IUnknown** ppManagedObject
);
```

```cpp
int GetManagedObject(
   out object ppManagedObject
);
```

## <a name="parameters"></a>Parâmetros
`ppManagedObject`\
[out] Retorna uma interface que representa o objeto gerenciado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 A interface retornada desse método pode ser consultada para qualquer interface implementada pela classe gerenciada, permitindo que seus métodos sejam chamados.

## <a name="see-also"></a>Consulte também
- [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)