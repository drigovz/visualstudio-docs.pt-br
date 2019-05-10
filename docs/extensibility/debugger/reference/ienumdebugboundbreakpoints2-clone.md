---
title: IEnumDebugBoundBreakpoints2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugBoundBreakpoints2::Clone
helpviewer_keywords:
- IEnumDebugBoundBreakpoints2::Clone
ms.assetid: c6ce01a2-7da3-46ec-9837-855042fa7244
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4d9295e13138340dbd430682adcde935832244df
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223277"
---
# <a name="ienumdebugboundbreakpoints2clone"></a>IEnumDebugBoundBreakpoints2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone(
   IEnumDebugBoundBreakpoints2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugBoundBreakpoints2 ppEnum
);
```

## <a name="parameters"></a>Parâmetros
 `ppEnum`\

 [out] Retorna uma cópia dessa enumeração como um objeto separado.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A cópia da enumeração tem o mesmo estado original no momento em que esse método é chamado. No entanto, a cópia e o original estados são separados e podem ser alterados individualmente.

## <a name="see-also"></a>Consulte também
- [IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)