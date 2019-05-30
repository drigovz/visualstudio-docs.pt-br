---
title: IEnumCodePaths2::Next | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Next
helpviewer_keywords:
- IEnumCodePaths2::Next
ms.assetid: c7a8fe97-2abc-4cee-8aef-64f1daa93b5c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8149c63a73b4d0a0981ab38455ac1fa48537c192
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310050"
---
# <a name="ienumcodepaths2next"></a>IEnumCodePaths2::Next
Retorna o próximo conjunto de elementos da enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Next(
   ULONG       celt,
   CODE_PATH** rgelt,
   ULONG*      pceltFetched
);
```

```csharp
int Next(
   uint        celt,
   CODE_PATH[] rgelt,
   ref uint    pceltFetched
);
```

## <a name="parameters"></a>Parâmetros
`celt`\
[in] O número de elementos a serem recuperados. Também especifica o tamanho máximo da `rgelt` matriz.

`rgelt`\
[no, out] Matriz de [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) elementos a serem preenchidos.

`pceltFetched`\
[out] Retorna o número de elementos realmente retornados em `rgelt`.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se menos do que o número solicitado de elementos podem ser retornados; caso contrário, retornará um código de erro.

## <a name="see-also"></a>Consulte também
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)