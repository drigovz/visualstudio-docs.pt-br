---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac21ac30e1f4511efa1ec8a7fe27129bf2ddb3a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321654"
---
# <a name="idebugarrayobjectgetcount"></a>IDebugArrayObject::GetCount
Obtém a contagem de elementos na matriz.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCount( 
   DWORD* pdwElements
);
```

```csharp
int GetCount(
   out uint pdwElements
);
```

## <a name="parameters"></a>Parâmetros
`pdwElements`\
[out] Retorna a contagem.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método vê todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo se o objeto de matriz é multidimensional. Por exemplo, dada a matriz `myarray[3][2][6]`, esse método retornaria 36 no `pdwElements` parâmetro. Use o [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) método para recuperar os elementos individuais um por vez.

## <a name="see-also"></a>Consulte também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)