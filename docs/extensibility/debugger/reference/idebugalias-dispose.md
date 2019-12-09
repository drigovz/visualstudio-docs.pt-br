---
title: IDebugAlias::Dispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c84fc6887eb2594f9665924bd3eafa5452a3135c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66330274"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marca este alias para remoção.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parâmetros
 nenhuma.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Depois que esse método é chamado, o alias não está mais disponível.

## <a name="see-also"></a>Consulte também
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)