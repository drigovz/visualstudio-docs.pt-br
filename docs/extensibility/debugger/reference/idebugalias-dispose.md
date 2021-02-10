---
title: IDebugAlias::D ispose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 033d74be9548b6bdaaccfe567e99c1d94453bca5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99944791"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Marca este alias para remoção.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parâmetros
 Nenhum.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois que esse método for chamado, o alias não estará mais disponível.

## <a name="see-also"></a>Consulte também
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
