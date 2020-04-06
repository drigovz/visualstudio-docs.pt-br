---
title: UNMANAGED_ADDRESS_PHYSICAL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UNMANAGED_ADDRESS_PHYSICAL
helpviewer_keywords:
- UNMANAGED_ADDRESS_PHYSICAL structure
ms.assetid: fed09686-caa6-4efc-851e-a0432019e9d0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9070fcfbf79fb96ecff87a793c221f3e7a65c2ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713281"
---
# <a name="unmanaged_address_physical"></a>UNMANAGED_ADDRESS_PHYSICAL
Esta estrutura representa um endereço físico.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagUNMANAGED_ADDRESS_PHYSICAL {
   ULONGLONG offset;
} UNMANAGED_ADDRESS_PHYSICAL;
```

```csharp
public struct UNMANAGED_ADDRESS_PHYSICAL {
   public ulong offset;
}
```

## <a name="members"></a>Membros
 `offset`\
 Um deslocamento de 64 bits em um espaço de endereço físico.

## <a name="remarks"></a>Comentários
 Essa estrutura faz parte da união na [estrutura DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) quando o `dwKind` campo da `DEBUG_ADDRESS_UNION` estrutura é definido para `ADDRESS_KIND_UNMANAGED_PHYSICAL` (um valor da enumeração [ADDRESS_KIND).](../../../extensibility/debugger/reference/address-kind.md)

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)
