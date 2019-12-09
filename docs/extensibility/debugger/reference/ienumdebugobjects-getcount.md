---
title: IEnumDebugObjects::GetCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::GetCount
helpviewer_keywords:
- IEnumDebugObjects::GetCount method
ms.assetid: 9cbc5db4-03ae-479f-a664-13cad66ad210
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 044aa63e10db74407754392299038623fd167631
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66339610"
---
# <a name="ienumdebugobjectsgetcount"></a>IEnumDebugObjects::GetCount
Esse método retorna o número de elementos na enumeração.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCount(
   [out] ULONG* pcelt
);
```

```csharp
int GetCount(
   out uint pcelt
);
```

## <a name="parameters"></a>Parâmetros
`pcelt`\
[out] Retorna o número de elementos na enumeração.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Esse método não é parte da interface habitual do enumeração COM qual especifica que somente Avançar, Clone, Skip e redefinição precisam ser implementados.

## <a name="see-also"></a>Consulte também
- [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)