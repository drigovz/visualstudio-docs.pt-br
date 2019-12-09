---
title: IDebugObject::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::GetSize
helpviewer_keywords:
- IDebugObject::GetSize method
ms.assetid: 89af423b-36eb-479d-b2de-2693455eca15
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 22d47ba6fdeb22ad44871d08419aa2e4990a83fc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66323599"
---
# <a name="idebugobjectgetsize"></a>IDebugObject::GetSize
Obtém o tamanho do objeto em bytes.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSize( 
   UINT* pnSize
);
```

```csharp
int GetSize(
   out uint pnSize
);
```

## <a name="parameters"></a>Parâmetros
`pnSize`\
[out] Retorna o tamanho em bytes.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Use o [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md) método para recuperar o valor como uma sequência de bytes.

## <a name="see-also"></a>Consulte também
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)