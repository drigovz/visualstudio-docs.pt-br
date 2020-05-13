---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82796c1d82dc3ca77151abcec3e1dd6ce13ac59d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713322"
---
# <a name="type_info"></a>TYPE_INFO
Esta estrutura especifica vários tipos de informações sobre o tipo de campo.

## <a name="syntax"></a>Sintaxe

```cpp
struct _tagTYPE_INFO_UNION {
   dwTYPE_KIND dwKind;
   union {
      METADATA_TYPE typeMeta;
      PDB_TYPE      typePdb;
      BUILT_TYPE    typeBuilt;
      DWORD         unused;
   } type;
} TYPE_INFO;
```

```csharp
public struct TYPE_INFO {
   public uint   dwKind;
   public IntPtr unionmember;
};
```

## <a name="members"></a>Membros
 `dwKind`\
 Um valor da [enumeração dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) que determina como interpretar a união.

 `type.typeMeta`\
 [Somente C++] Contém uma estrutura `dwKind` `TYPE_KIND_METADATA` [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) se for .

 `type.typePdb`\
 [Somente C++] Contém uma estrutura `dwKind` `TYPE_KIND_PDB` [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) se for .

 `type.typeBuilt`\
 [Somente C++] Contém uma estrutura `dwKind` `TYPE_KIND_BUILT` [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) se for .

 `type.unused`\
 Estofamento não utilizado.

 `type`\
 Nome do sindicato.

 `unionmember`\
 [C# apenas] Marechal isso para o tipo `dwKind`de estrutura apropriada com base em .

## <a name="remarks"></a>Comentários
 Essa estrutura é passada para o método [GetTypeInfo,](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) onde é preenchida. A forma como o conteúdo da `dwKind` estrutura é interpretado é baseada no campo.

> [!NOTE]
> [Somente C++] Se `dwKind` for `TYPE_KIND_BUILT`igual, então é necessário liberar o objeto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) subjacente ao destruir a `TYPE_INFO` estrutura. Isso é feito chamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# apenas] A tabela a seguir `unionmember` mostra como interpretar o membro para cada tipo de tipo. O Exemplo mostra como isso é feito para um tipo de tipo.

|`dwKind`|`unionmember`interpretado como|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Exemplo
 Este exemplo mostra como `unionmember` interpretar `TYPE_INFO` o membro da estrutura em C#. Este exemplo mostra interpretar apenas`TYPE_KIND_METADATA`um tipo ( ) mas os outros são interpretados exatamente da mesma maneira.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(TYPE_INFO ti)
        {
            if (ti.dwKind == (uint)enum_dwTypeKind.TYPE_KIND_METADATA)
            {
                 METADATA_TYPE dataType = (METADATA_TYPE)Marshal.PtrToStructure(ti.unionmember,
                                               typeof(METADATA_TYPE));
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
 Cabeçalho: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [Gettypeinfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)
