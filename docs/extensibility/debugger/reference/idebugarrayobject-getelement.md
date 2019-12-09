---
title: IDebugArrayObject::GetElement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetElement
helpviewer_keywords:
- IDebugArrayObject::GetElement method
ms.assetid: 08b44341-7bf1-4a8c-8b79-98ae5785b195
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 527302a2e6d6fc2884107e3773402adc56b881c7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322215"
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

## <a name="parameters"></a>Parâmetros
`dwIndex`\
[in] O índice do elemento.

`ppElement`\
[out] Retorna um [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) interface que representa o elemento.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método vê todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo se o objeto de matriz é multidimensional. Por exemplo, dada a matriz `myarray[3][2][6]` e uma `dwIndex` parâmetro de 20, esse método retornará o elemento de `myarray[1][1][2]`e uma `dwIndex` parâmetro 21 retornaria o elemento do `myarray[1][1][3]`. Use o [GetCount](../../../extensibility/debugger/reference/idebugarrayobject-getcount.md) método para determinar o número total de elementos na matriz.

## <a name="see-also"></a>Consulte também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)