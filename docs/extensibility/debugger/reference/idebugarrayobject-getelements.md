---
title: IDebugArrayObject::GetElements | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElements
helpviewer_keywords:
- IDebugArrayObject::GetElements method
ms.assetid: f6a6262f-5183-46ce-8a45-33ef46088b98
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bae57db294d52eb476baa32b63e27c6e8b287071
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65615331"
---
# <a name="idebugarrayobjectgetelements"></a>IDebugArrayObject::GetElements
Obtém um enumerador de todos os elementos da matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetElements( 
   IEnumDebugObjects** ppEnum
);
```

```csharp
int GetElements(
   out IEnumDebugObjects ppEnum
);
```

## <a name="parameters"></a>Parâmetros
`ppEnum`\
[out] Retorna um [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) objeto que permite enumerar em todos os elementos.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Como alternativa, use o [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) métodos para iterar por meio de elementos.

## <a name="see-also"></a>Consulte também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)