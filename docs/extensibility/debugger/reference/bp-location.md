---
title: BP_LOCATION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_LOCATION
helpviewer_keywords:
- BP_LOCATION union
ms.assetid: ed1e874c-f289-4c31-8b6c-04dde03ad0f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c98fde516a3e836302cd7eb2c73abd730d5cc8c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737935"
---
# <a name="bp_location"></a>BP_LOCATION
Especifica o tipo de estrutura usada para descrever a localização do ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_LOCATION {
    BP_LOCATION_TYPE bpLocationType;
    union {
        BP_LOCATION_CODE_FILE_LINE   bplocCodeFileLine;
        BP_LOCATION_CODE_FUNC_OFFSET bplocCodeFuncOffset;
        BP_LOCATION_CODE_CONTEXT     bplocCodeContext;
        BP_LOCATION_CODE_STRING      bplocCodeString;
        BP_LOCATION_CODE_ADDRESS     bplocCodeAddress;
        BP_LOCATION_DATA_STRING      bplocDataString;
        BP_LOCATION_RESOLUTION       bplocResolution;
        DWORD                        unused;
    } bpLocation;
} BP_LOCATION;
```

```csharp
public struct BP_LOCATION {
    public uint   bpLocationType;
    public IntPtr unionmember1;
    public IntPtr unionmember2;
    public IntPtr unionmember3;
    public IntPtr unionmember4;
};
```

## <a name="members"></a>Membros
`bpLocationType`\
Um valor da [enumeração BP_LOCATION_TYPE](../../../extensibility/debugger/reference/bp-location-type.md) `bpLocation` utilizado para `unionmemberX` interpretar o sindicato ou os membros.

`bpLocation`.`bplocCodeFileLine`\
[Somente C++] Contém [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) a estrutura `bpLocationType`  =  `BPLT_CODE_FILE_LINE`BP_LOCATION_CODE_FILE_LINE se .

`bpLocation.bplocCodeFuncOffset`\
[Somente C++] Contém [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) a estrutura `bpLocationType`  =  `BPLT_CODE_FUNC_OFFSET`BP_LOCATION_CODE_FUNC_OFFSET se .

`bpLocation.bplocCodeContext`\
[Somente C++] Contém [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) a estrutura `bpLocationType`  =  `BPLT_CODE_CONTEXT`BP_LOCATION_CODE_CONTEXT se .

`bpLocation.bplocCodeString`\
[Somente C++] Contém [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) a estrutura `bpLocationType`  =  `BPLT_CODE_STRING`BP_LOCATION_CODE_STRING se .

`bpLocation.bplocCodeAddress`\
[Somente C++] Contém [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) a estrutura `bpLocationType`  =  `BPLT_CODE_ADDRESS`BP_LOCATION_CODE_ADDRESS se .

`bpLocation.bplocDataString`\
[Somente C++] Contém [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) a estrutura `bpLocationType`  =  `BPLT_DATA_STRING`BP_LOCATION_DATA_STRING se .

`bpLocation.bplocResolution`\
[Somente C++] Contém [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) a estrutura `bpLocationType`  =  `BPLT_RESOLUTION`BP_LOCATION_RESOLUTION se .

`unionmember1`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember2`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember3`\
[C# apenas] Veja observações sobre como interpretar.

`unionmember4`\
[C# apenas] Veja observações sobre como interpretar.

## <a name="remarks"></a>Comentários
Esta estrutura é um membro das estruturas [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

 [C# apenas] Os `unionmemberX` membros são interpretados de acordo com a tabela a seguir. Procure a coluna esquerda `bpLocationType` para obter o valor e, `unionmemberX` em seguida, olhe `unionmemberX` através das outras colunas para determinar o que cada membro representa e marechal o em conformidade. Veja o exemplo de uma maneira de interpretar uma parte desta estrutura em C#.

|`bpLocationType`|`unionmember1`|`unionmember2`|`unionmember3`|`unionmember4`|
|----------------------|--------------------|--------------------|--------------------|--------------------|
|`BPLT_CODE_FILE_LINE`|`string`(um contexto)|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|-|-|
|`BPLT_CODE_FUNC_OFFSET`|`string`(um contexto)|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|-|-|
|`BPLT_CODE_CONTEXT`|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|-|-|-|
|`BPLT_CODE_STRING`|`string`(um contexto)|`string`(expressão condicional)|-|-|
|`BPLT_CODE_ADDRESS`|`string`(um contexto)|`string`(URL do módulo)|`string`(nome da função)|`string`(endereço)|
|`BPLT_DATA_STRING`|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|`string`(um contexto)|`string`(expressão de dados)|`uint`(número de elementos)|
|`BPLT_RESOLUTION`|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|-|-|-|

## <a name="example"></a>Exemplo
Este exemplo mostra como `BP_LOCATION` interpretar a estrutura `BPLT_DATA_STRING` em C# para o tipo. Este tipo em particular mostra `unionmemberX` como interpretar todos os quatro membros em todos os formatos possíveis (objeto, seqüência e número).

```csharp
using System;
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio.Debugger.Interop;

namespace MyPackage
{
    public class MyClass
    {
        public void Interpret(BP_LOCATION bp)
        {
            if (bp.bpLocationType == (uint)enum_BP_LOCATION_TYPE.BPLT_DATA_STRING)
            {
                IDebugThread2 pThread = (IDebugThread2)Marshal.GetObjectForIUnknown(bp.unionmember1);
                string context = Marshal.PtrToStringBSTR(bp.unionmember2);
                string dataExpression = Marshal.PtrToStringBSTR(bp.unionmember3);
                uint numElements = (uint)Marshal.ReadInt32(bp.unionmember4);
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
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)
- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)
- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)
- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)
- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)
- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)
