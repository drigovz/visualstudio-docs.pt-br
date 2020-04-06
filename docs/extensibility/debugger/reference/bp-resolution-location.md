---
title: BP_RESOLUTION_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_LOCATION
helpviewer_keywords:
- BP_RESOLUTION_LOCATION structure
ms.assetid: 21dc5246-69c1-43e3-855c-9cd4e596c0e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b11d80e90daec19a14ca509e5a4b9bdb2d1ced4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737816"
---
# <a name="bp_resolution_location"></a>BP_RESOLUTION_LOCATION
Especifica a estrutura do local de resolução do ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
struct _BP_RESOLUTION_LOCATION {
    BP_TYPE bpType;
    union {
        BP_RESOLUTION_CODE bpresCode;
        BP_RESOLUTION_DATA bpresData;
        int                unused;
    } bpResLocation;
} BP_RESOLUTION_LOCATION;
```

```csharp
public struct BP_RESOLUTION_LOCATION {
    public uint   bpType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public uint   unionmember4;
};
```

## <a name="members"></a>Membros
`bpType`\
Um valor da [enumeração BP_TYPE](../../../extensibility/debugger/reference/bp-type.md) que especifica `bpResLocation` como `unionmemberX` interpretar o sindicato ou os membros.

`bpResLocation.bpresCode`\
[Somente C++] Contém [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) a estrutura `bpType`  =  `BPT_CODE`BP_RESOLUTION_CODE se .

`bpResLocation.bpresData`\
[Somente C++] Contém [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) a estrutura `bpType`  =  `BPT_DATA`BP_RESOLUTION_DATA se .

`bpResLocation.unused`\
[Somente C++] Um espaço reservado.

`unionmember1`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember2`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember3`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember4`\
[C# apenas] Veja observações sobre como interpretar.

## <a name="remarks"></a>Comentários
Essa estrutura é membro das estruturas [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) e [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

 [C# apenas] Os `unionmemberX` membros são interpretados de acordo com a tabela a seguir. Procure a coluna esquerda `bpType` para o valor, `unionmemberX` em seguida, `unionmemberX` através para determinar o que cada membro representa e marechal o em conformidade. Veja o Exemplo para uma maneira de interpretar essa estrutura em C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPT_CODE`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPT_DATA`|`string`(expressão de dados)|`string`(nome da função)|`string`(nome da imagem)|`enum_BP_RES_DATA_FLAGS`|

## <a name="example"></a>Exemplo
Este exemplo mostra como `BP_RESOLUTION_LOCATION` interpretar a estrutura em C#.

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_RESOLUTION_LOCATION bprl)
        {
            if (bprl.bpType == (uint)enum_BP_TYPE.BPT_CODE)
            {
                IDebugCodeContext2 pContext = (IDebugCodeContext2)Marshal.GetObjectForIUnknown(bp.unionmember1);
            }
            else if (bprl.bpType == (uint)enum_BP_TYPE.BPT_DATA)
            {
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                string functionName = Marshal.PtrToStringBSTR(bp.unionmember2);
                string imageName = Marshal.PtrToStringBSTR(bp.unionmember3);
                enum_BP_RES_DATA_FLAGS numElements = (enum_BP_RES_DATA_FLAGS)bp.unionmember4;
            }
        }
    }
}
```

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_TYPE](../../../extensibility/debugger/reference/bp-type.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)
- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)
- [BP_RES_DATA_FLAGS](../../../extensibility/debugger/reference/bp-res-data-flags.md)
