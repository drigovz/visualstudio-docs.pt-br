---
title: IDebugPointerObject::Dereference | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f01e863d03f6179ef4c15f50521cc72ba21f5740
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56706581"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Obtém o objeto apontado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

#### <a name="parameters"></a>Parâmetros
 `dwIndex`

 [in] Um deslocamento de byte simples desde o início do objeto apontado.

 `ppObject`

 [out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) do objeto que representa o objeto apontado, e o deslocamento, se houver.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro. Retornará E_FAIL se este objeto não apontar para outro objeto.

## <a name="remarks"></a>Comentários
 O objeto apontado pode ser um primitivo ou um tipo mais complexo, como uma classe ou estrutura.

## <a name="see-also"></a>Consulte também
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)