---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ea46939118ec48490280d6a85cc84e144d320d4e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737736"
---
# <a name="bpreqi_fields90"></a>BPREQI_FIELDS90
Enumera os valores válidos que especificam as informações a serem recuperadas sobre uma solicitação de ponto de ruptura. Essa enumeração estende a [enumeração BPREQI_FIELDS.](../../../extensibility/debugger/reference/bpreqi-fields.md)

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
typedef DWORD BPREQI_FIELDS90;
```

```csharp
public enum enum_BPREQI_FIELDS90
{
    // VS 8.0 values
    BPREQI90_BPLOCATION                = 0x0001,
    BPREQI90_LANGUAGE                  = 0x0002,
    BPREQI90_PROGRAM                   = 0x0004,
    BPREQI90_PROGRAMNAME               = 0x0008,
    BPREQI90_THREAD                    = 0x0010,
    BPREQI90_THREADNAME                = 0x0020,
    BPREQI90_PASSCOUNT                 = 0x0040,
    BPREQI90_CONDITION                 = 0x0080,
    BPREQI90_FLAGS                     = 0x0100,
    BPREQI90_ALLOLDFIELDS              = 0x01ff,
    BPREQI90_VENDOR                    = 0x0200,
    BPREQI90_CONSTRAINT                = 0x0400,
    BPREQI90_TRACEPOINT                = 0x0800,

    // Values added in VS 9.0
    BPREQI90_MACROTRACEPOINT           = 0x1000,

    BPREQI90_ALLFIELDS                 = 0xffff
};
```

## <a name="fields"></a>Campos
`BPREQI90_BPLOCATION`\
Inicialize ou `bpLocation` use o campo (localização de ponto de ruptura) da estrutura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI90_LANGUAGE`\
Inicialize ou `guidLanguage` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_PROGRAM`\
Inicialize ou `pProgram` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_PROGRAMNAME`\
Inicialize ou `bstrProgramName` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_THREAD`\
Inicialize ou `pThread` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_THREADNAME`\
Inicialize ou `bstrThreadName` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_PASSCOUNT`\
Inicialize ou `bpPassCount` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_CONDITION`\
Inicialize ou `bpCondition` use o campo (condição `BP_REQUEST_INFO` `BP_REQUEST_INFO2` de ponto de ruptura) da ou estrutura.

`BPREQI90_FLAGS`\
Inicialize ou `dwFlags` use o `BP_REQUEST_INFO` `BP_REQUEST_INFO2` campo da ou estrutura.

`BPREQI90_ALLOLDFIELDS`\
Inicialize ou use todos os `BP_REQUEST_INFO` campos para a estrutura.

`BPREQI90_VENDOR`\
Inicialize ou `guidVendor` use `BP_REQUEST_INFO2` o campo de estrutura.

`BPREQI90_CONSTRAINT`\
Inicialize ou `bstrConstraint` use `BP_REQUEST_INFO2` o campo de estrutura.

`BPREQI90_TRACEPOINT`\
Inicialize ou `bstrTracepoint` use `BP_REQUEST_INFO2` o campo de estrutura.

`BPREQI90_MACROTRACEPOINT`\
Inicialize ou `bstrMacroTracepoint` use `BP_REQUEST_INFO2` o campo de estrutura. BPREQI_ALLFIELDS não inclui este campo.

`BPREQI90_ALLFIELDS`\
Especifica todos os `BP_REQUEST_INFO2` campos para a estrutura.

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
