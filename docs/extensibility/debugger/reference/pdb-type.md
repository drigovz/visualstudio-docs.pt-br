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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1f736d7d9b190fc46945e2f4f7c309b88c3e851f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714101"
---
# <a name="pdb_type"></a>PDB_TYPE

Esta estrutura especifica informações sobre um tipo de campo retirado de um símbolo PDB.

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
ID do aplicativo de onde veio o símbolo. Isso é usado para identificar exclusivamente uma instância do aplicativo.

`guidModule`\
O GUID do módulo que contém este campo.

`symid`\
O ID do símbolo que corresponde a este campo.

## <a name="remarks"></a>Comentários

Essa estrutura aparece como parte da união `dwKind` na estrutura `TYPE_INFO` [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) quando `TYPE_KIND_PDB` o campo da estrutura é definido para (um valor da [enumeração dwTYPE_KIND).](../../../extensibility/debugger/reference/dwtype-kind.md)

## <a name="requirements"></a>Requisitos

Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também

- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
