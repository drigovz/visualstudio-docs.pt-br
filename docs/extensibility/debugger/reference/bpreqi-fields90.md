---
title: BPREQI_FIELDS90 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- BPREQI_FIELDS90 enumeration
ms.assetid: bf6f7efc-39f2-46a2-906d-c3647bf89995
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be07e034b4059ae7ade40a5a248c01bc4a8237b8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695928"
---
# <a name="bpreqifields90"></a>BPREQI_FIELDS90
Enumera os valores válidos que especificam as informações a serem recuperados sobre uma solicitação de ponto de interrupção. Esta enumeração estende o [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) enumeração.

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

#### <a name="parameters"></a>Parâmetros
Inicializar BPREQI90_BPLOCATION ou usar o `bpLocation` campo (localização do ponto de interrupção) a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura.

Inicializar BPREQI90_LANGUAGE ou usar o `guidLanguage` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_PROGRAM ou usar o `pProgram` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_PROGRAMNAME ou usar o `bstrProgramName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_THREAD ou usar o `pThread` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_THREADNAME ou usar o `bstrThreadName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_PASSCOUNT ou usar o `bpPassCount` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_CONDITION ou usar o `bpCondition` campo (condição de ponto de interrupção) da `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_FLAGS ou usar o `dwFlags` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_ALLOLDFIELDS ou use todos os campos para o do `BP_REQUEST_INFO` estrutura.

Inicializar BPREQI90_VENDOR ou usar o `guidVendor` campo de `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_CONSTRAINT ou usar o `bstrConstraint` campo de `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_TRACEPOINT ou usar o `bstrTracepoint` campo de `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI90_MACROTRACEPOINT ou usar o `bstrMacroTracepoint` campo de `BP_REQUEST_INFO2` estrutura. BPREQI_ALLFIELDS não incluir esse campo.

BPREQI90_ALLFIELDS especifica todos os campos para o `BP_REQUEST_INFO2` estrutura.

## <a name="requirements"></a>Requisitos
Cabeçalho: Msdbg90.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
