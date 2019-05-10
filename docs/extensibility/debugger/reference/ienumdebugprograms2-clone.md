---
title: IEnumDebugPrograms2::Clone | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2::Clone
helpviewer_keywords:
- IEnumDebugPrograms2::Clone
ms.assetid: 880846c2-39d3-45cd-85c3-ad5409a3710f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 793c3affd4f4b7cca4ac51ff0a585d9d76179d43
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65223500"
---
# <a name="ienumdebugprograms2clone"></a>IEnumDebugPrograms2::Clone
Retorna uma cópia da enumeração atual como um objeto separado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Clone(
   IEnumDebugPrograms2** ppEnum
);
```

```csharp
int Clone(
   out IEnumDebugPrograms2 ppEnum
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
- [IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)