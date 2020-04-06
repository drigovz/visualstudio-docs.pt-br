---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e29fe09905119057224b45b455e4f56e5ce904af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736176"
---
# <a name="idebugarrayobjectgetelement"></a>IDebugArrayObject::GetElement
Obtém um elemento da matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetElement( 
   DWORD          dwIndex,
   IDebugObject** ppElement
);
```

```csharp
int GetElement(
   [In] uint dwIndex,
   out IDebugObject ppElement
);
```

## <a name="parameters"></a>parâmetros
`dwIndex`\
[em] O índice de elementos.

`ppElement`\
[fora] Retorna uma interface [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) que representa o elemento.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método vê todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo que o objeto de matriz seja multidimensional. Por exemplo, dada `myarray[3][2][6]` `dwIndex` a matriz e um parâmetro de 20, este método retornaria o elemento de `myarray[1][1][2]`, e um `dwIndex` parâmetro de 21 retornaria o elemento de `myarray[1][1][3]`. Use o método [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) para determinar o número total de elementos na matriz.

## <a name="see-also"></a>Confira também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
