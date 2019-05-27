---
title: TYPE_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TYPE_INFO
helpviewer_keywords:
- TYPE_INFO structure
ms.assetid: d725cb68-a565-49d1-a16f-ff0445c587a0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9edb111c15c83fc6da8df2cea1eed96aed9252b0
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212695"
---
# <a name="typeinfo"></a>TYPE_INFO
Essa estrutura especifica vários tipos de informações sobre o tipo de um campo.

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
 Um valor a partir de [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeração que determina como interpretar a união.

 `type.typeMeta`\
 [C++ somente] Contém uma [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estrutura se `dwKind` é `TYPE_KIND_METADATA`.

 `type.typePdb`\
 [C++ somente] Contém uma [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estrutura se `dwKind` é `TYPE_KIND_PDB`.

 `type.typeBuilt`\
 [C++ somente] Contém uma [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estrutura se `dwKind` é `TYPE_KIND_BUILT`.

 `type.unused`\
 Preenchimento não utilizado.

 `type`\
 Nome da união.

 `unionmember`\
 [C# somente] Marshaling para o tipo de estrutura apropriada com base em `dwKind`.

## <a name="remarks"></a>Comentários
 Essa estrutura é passada para o [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método onde ele é preenchido. Como o conteúdo da estrutura é interpretado se baseia o `dwKind` campo.

> [!NOTE]
> [C++ somente] Se `dwKind` é igual a `TYPE_KIND_BUILT`, em seguida, é necessário liberar subjacente [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) do objeto ao destruir o `TYPE_INFO` estrutura. Isso é feito chamando `typeInfo.type.typeBuilt.pUnderlyingField->Release()`.

 [C# somente] A tabela a seguir mostra como interpretar o `unionmember` membro para cada tipo do tipo. O exemplo mostra como isso é feito para um tipo de tipo.

|`dwKind`|`unionmember` interpretado como|
|--------------|----------------------------------|
|`TYPE_KIND_METADATA`|[METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)|
|`TYPE_KIND_PDB`|[PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)|
|`TYPE_KIND_BUILT`|[BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)|

## <a name="example"></a>Exemplo
 Este exemplo mostra como interpretar a `unionmember` membro o `TYPE_INFO` estrutura em c#. Este exemplo mostra apenas um tipo de interpretação (`TYPE_KIND_METADATA`), mas os outros são interpretados exatamente da mesma maneira.

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
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
- [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)
- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)
- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)
- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)