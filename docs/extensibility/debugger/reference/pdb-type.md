---
title: PDB_TYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- PDB_TYPE
helpviewer_keywords:
- PDB_TYPE structure
ms.assetid: 1c1bb772-77d6-4870-90b2-fd9247d0004e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df6a41801f4cce272d896776745ac0cc507d0e38
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890013"
---
# <a name="pdb_type"></a>PDB_TYPE

Essa estrutura especifica informações sobre um tipo de campo extraído de um símbolo PDB.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _tagTYPE_PDB {
    ULONG32 ulAppDomainID;
    GUID    guidModule;
    DWORD   symid;
} PDB_TYPE;
```

```csharp
public struct PDB_TYPE {
    public uint ulAppDomainID;
    public Guid guidModule;
    public uint symid;
};
```

## <a name="members"></a>Membros

`ulAppDomainID`\
ID do aplicativo do qual o símbolo veio. Isso é usado para identificar exclusivamente uma instância do aplicativo.

`guidModule`\
O GUID do módulo que contém este campo.

`symid`\
A ID do símbolo que corresponde a esse campo.

## <a name="remarks"></a>Comentários

Essa estrutura aparece como parte da União na estrutura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando o `dwKind` campo da `TYPE_INFO` estrutura é definido como `TYPE_KIND_PDB` (um valor da enumeração [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).

## <a name="requirements"></a>Requisitos

Cabeçalho: sh. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também

- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
