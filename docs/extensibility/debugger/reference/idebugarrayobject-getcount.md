---
title: IDebugArrayObject::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetCount
helpviewer_keywords:
- IDebugArrayObject::GetCount method
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d9d5e322b7bcd5238335c74caa21989f1f1962ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736205"
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

## <a name="parameters"></a>parâmetros
`pdwElements`\
[fora] Retorna a contagem.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método vê todos os elementos de um objeto de matriz como uma matriz unidimensional, mesmo que o objeto de matriz seja multidimensional. Por exemplo, dada a matriz, `myarray[3][2][6]`este `pdwElements` método retornaria 36 no parâmetro. Use o método [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md) para recuperar os elementos individuais um de cada vez.

## <a name="see-also"></a>Confira também
- [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
