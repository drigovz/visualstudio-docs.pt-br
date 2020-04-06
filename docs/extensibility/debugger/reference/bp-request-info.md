---
title: BP_REQUEST_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_REQUEST_INFO
helpviewer_keywords:
- BP_REQUEST_INFO structure
ms.assetid: 42a31412-5b6b-47fe-a762-0c2bc769e1cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 35a1202f4990f4f6370ad031c896ba85ebb6d816
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737887"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Contém as informações necessárias para implementar um ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_REQUEST_INFO {
    BPREQI_FIELDS   dwFields;
    GUID            guidLanguage;
    BP_LOCATION     bpLocation;
    IDebugProgram2* pProgram;
    BSTR            bstrProgramName;
    IDebugThread2*  pThread;
    BSTR            bstrThreadName;
    BP_CONDITION    bpCondition;
    BP_PASSCOUNT    bpPassCount;
    BP_FLAGS        dwFlags;
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
    public uint           dwFields;
    public Guid           guidLanguage;
    public BP_LOCATION    bpLocation;
    public IDebugProgram2 pProgram;
    public string         bstrProgramName;
    public IDebugThread2  pThread;
    public string         bstrThreadName;
    public BP_CONDITION   bpCondition;
    public BP_PASSCOUNT   bpPassCount;
    public uint           dwFlags;
};
```

## <a name="members"></a>Membros
`dwFields`\
Uma combinação de bandeiras da enumeração [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica quais campos são preenchidos.

`guidLanguage`\
O GUID do idioma.

`bpLocation`\
A estrutura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica o tipo de local do ponto de ruptura.

`pProgram`\
O objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o aplicativo no qual ocorre o ponto de ruptura.

`bstrProgramName`\
O nome do aplicativo no qual ocorre o ponto de ruptura.

`pThread`\
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento no qual ocorre o ponto de ruptura.

`bstrThreadName`\
O nome do segmento no qual ocorre o ponto de ruptura.

`bpCondition`\
A [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) estrutura que descreve as condições sob as quais o ponto de ruptura será acionado.

`bpPassCount`\
A [estrutura BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contém as informações de contagem de passes do ponto de ruptura.

`dwFlags`\
Uma combinação de bandeiras da enumeração [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica as bandeiras para o ponto de ruptura solicitado.

## <a name="remarks"></a>Comentários
Essa estrutura é devolvida pelo método [GetRequestInfo.](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)

Se você precisar obter o GUID do fornecedor do motor de depuração, a restrição de ponto de ruptura ou o ponto de rastreamento, consulte a estrutura [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)
- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
