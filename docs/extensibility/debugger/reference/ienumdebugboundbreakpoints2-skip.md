---
title: IEnumDebugBoundBreakpoints2::Skip | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Skip
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Skip
ms.assetid: 95659709-6d7c-44ca-b598-629eb688429f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a34decbeeaa4c0208eb803f48553fbfd18ad0eb9
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223455"
---
# <a name="ienumdebugboundbreakpoints2skip"></a>IEnumDebugBoundBreakpoints2::Skip
Ignora o número especificado de elementos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Skip(
   ULONG celt
);
```

```csharp
int Skip(
   uint celt
);
```

## <a name="parameters"></a>Parâmetros
 `celt`\

 [in] Número de elementos a serem ignorados.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`. Retorna `S_FALSE` se `celt` é maior que o número de elementos restantes; caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Se `celt` Especifica um valor maior que o número de elementos restantes, a enumeração é definida como o fim e `S_FALSE` é retornado.

## <a name="see-also"></a>Consulte também
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)