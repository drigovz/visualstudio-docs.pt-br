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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c806687b9948be693ca25868aaf7211d9ccf6b97
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902023"
---
# <a name="bp_request_info"></a>BP_REQUEST_INFO
Contém as informações necessárias para implementar um ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_REQUEST_INFO {
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
} BP_REQUEST_INFO;
```

```csharp
public struct BP_REQUEST_INFO {
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
Uma combinação de sinalizadores da enumeração [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) que especifica quais campos são preenchidos.

`guidLanguage`\
O GUID do idioma.

`bpLocation`\
A estrutura de [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) que especifica o tipo do local do ponto de interrupção.

`pProgram`\
O objeto [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) que representa o aplicativo no qual ocorre o ponto de interrupção.

`bstrProgramName`\
O nome do aplicativo no qual ocorre o ponto de interrupção.

`pThread`\
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread no qual o ponto de interrupção ocorre.

`bstrThreadName`\
O nome do thread no qual o ponto de interrupção ocorre.

`bpCondition`\
A estrutura de [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que descreve as condições sob as quais o ponto de interrupção será acionado.

`bpPassCount`\
A estrutura de [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que contém as informações de contagem de aprovação do ponto de interrupção.

`dwFlags`\
Uma combinação de sinalizadores da enumeração [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) que especifica os sinalizadores para o ponto de interrupção solicitado.

## <a name="remarks"></a>Comentários
Essa estrutura é retornada pelo método [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) .

Se você precisar obter o GUID do fornecedor do mecanismo de depuração, a restrição de ponto de interrupção ou o tracepoint, consulte a estrutura de [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

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
