---
title: BP_RESOLUTION_DATA | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_RESOLUTION_DATA
helpviewer_keywords:
- BP_RESOLUTION_DATA structure
ms.assetid: 9e0b9000-6a84-47b9-b07a-367a75764389
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 93a78f84c10af047e596459b68211b885d3c3085
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737847"
---
# <a name="bp_resolution_data"></a>BP_RESOLUTION_DATA
Descreve o resultado da vinculação de um ponto de ruptura de dados.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_RESOLUTION_DATA {
    BSTR              bstrDataExpr;
    BSTR              bstrFunc;
    BSTR              bstrImage;
    BP_RES_DATA_FLAGS dwFlags;
} BP_RESOLUTION_DATA;
```

```csharp
public struct BP_RESOLUTION_DATA {
    public string bstrDataExpr;
    public string bstrFunc;
    public string bstrImage;
    public uint   dwFlags;
};
```

## <a name="members"></a>Membros
`bstrDataExpr`\
A expressão de dados que foi vinculada.

`bstrFunc`\
O nome da função que o ponto de ruptura de dados vinculou (se houver).

`bstrImage`\
O nome do módulo (MyModule.dll, por exemplo) que o ponto de ruptura de dados se limitou.

`dwFlags`\
Um valor da [enumeração BP_RES_DATA_FLAGS,](../../../extensibility/debugger/reference/bp-res-data-flags.md) descrevendo como o ponto de ruptura de dados é implementado.

## <a name="remarks"></a>Comentários
Essa estrutura é membro da estrutura [BP_RESOLUTION_LOCATION,](../../../extensibility/debugger/reference/bp-resolution-location.md) que por sua vez é membro da estrutura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devolvida pelo método [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
