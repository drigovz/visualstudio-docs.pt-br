---
title: iEnumCodePaths2::Reset | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2392c25513b53137e5cdca332bc133ab998be999
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717799"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Redefine a enumeração para o primeiro elemento.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Depois que este método é chamado, a próxima chamada para o método [Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) retorna o primeiro elemento da enumeração.

## <a name="see-also"></a>Confira também
- [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
