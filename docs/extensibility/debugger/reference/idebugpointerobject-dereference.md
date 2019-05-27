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
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 90a5a1f6fca718397654e836f41089b122425f0f
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209376"
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

## <a name="parameters"></a>Parâmetros
`dwIndex`\
[in] Um deslocamento de byte simples desde o início do objeto apontado.

`ppObject`\
[out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) do objeto que representa o objeto apontado, e o deslocamento, se houver.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro. Retornará E_FAIL se este objeto não apontar para outro objeto.

## <a name="remarks"></a>Comentários
 O objeto apontado pode ser um primitivo ou um tipo mais complexo, como uma classe ou estrutura.

## <a name="see-also"></a>Consulte também
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)