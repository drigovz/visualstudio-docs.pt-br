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
ms.openlocfilehash: cad81d76e2fcec01fa50a37fa6ab6cb49cfc79be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423693"
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

#### <a name="parameters"></a>Parâmetros
 `ppEnum`

 [out] Retorna um [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md) objeto que permite enumerar em todos os elementos.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Como alternativa, use o [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) e [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) métodos para iterar por meio de elementos.

## <a name="see-also"></a>Consulte também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)