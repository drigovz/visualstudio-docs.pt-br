---
title: dwTYPE_KIND | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a9d790f12d3fc21bbae7373470746af2ebfe6dc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737185"
---
# <a name="dwtype_kind"></a>dwTYPE_KIND
Especifica como interpretar o tipo de objeto [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};

typedef DWORD dwTYPE_KIND;
```

```csharp
public enum enum_dwTYPE_KIND {
    TYPE_KIND_METADATA = 0x0001,
    TYPE_KIND_PDB      = 0x0002,
    TYPE_KIND_BUILT    = 0x0003,
};
```

## <a name="fields"></a>Campos
`TYPE_KIND_METADATA`\
A [união TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) deve ser interpretada como uma estrutura [METADATA_TYPE.](../../../extensibility/debugger/reference/metadata-type.md)

`TYPE_KIND_PDB`\
A `TYPE_INFO` união deve ser interpretada como uma estrutura [PDB_TYPE.](../../../extensibility/debugger/reference/pdb-type.md)

`TYPE_KIND_BUILT`\
A `TYPE_INFO` união deve ser interpretada como uma [estrutura BUILT_TYPE.](../../../extensibility/debugger/reference/built-type.md)

## <a name="remarks"></a>Comentários
Os valores dessa enumeração `dwKind` aparecem no campo da [estrutura TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) e `type` são utilizados para determinar como interpretar o membro do sindicato. A `TYPE_INFO` estrutura é devolvida por uma chamada para o método [GetTypeInfo.](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)
- [Gettypeinfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
