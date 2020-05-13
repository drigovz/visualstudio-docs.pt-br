---
title: BP_ERROR_RESOLUTION_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d48c4bc888db0ad8be6a0d6e98eeea2223a27e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738092"
---
# <a name="bp_error_resolution_info"></a>BP_ERROR_RESOLUTION_INFO
Descreve a resolução de um ponto de ruptura de erro, incluindo localização, programa e segmento.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_ERROR_RESOLUTION_INFO {
    BPERESI_FIELDS         dwFields;
    BP_RESOLUTION_LOCATION bpResLocation;
    IDebugProgram2*        pProgram;
    IDebugThread2*         pThread;
    BSTR                   bstrMessage;
    BP_ERROR_TYPE          dwType;
} BP_ERROR_RESOLUTION_INFO;
```

```csharp
public struct BP_ERROR_RESOLUTION_INFO {
    public uint                   dwFields;
    public BP_RESOLUTION_LOCATION bpResLocation;
    public IDebugProgram2         pProgram;
    public IDebugThread2          pThread;
    public string                 bstrMessage;
    public uint                   dwType;
};
```

## <a name="members"></a>Membros
`dwFields`\
Uma combinação de valores da enumeração [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) especificando quais campos desta estrutura são preenchidos.

`bpResLocation`\
O [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) união, que especifica o local de resolução do ponto de ruptura.

`pProgram`\
O objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o aplicativo no qual ocorreu o erro de ponto de quebra.

`pThread`\
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento no qual o aplicativo que gerou o erro de ponto de quebra está sendo executado.

`bstrMessage`\
Uma seqüência contendo qualquer mensagem de aviso ou erro resultante desta resolução de erro.

`dwType`\
Um valor da enumeração [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) que especifica o tipo de erro de ponto de ruptura.

## <a name="remarks"></a>Comentários
Essa estrutura é devolvida a partir do método [GetResolutionInfo.](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
- [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)
- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)
