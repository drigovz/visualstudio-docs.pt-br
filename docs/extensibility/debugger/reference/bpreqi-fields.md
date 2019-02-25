---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 25b95e2934de9d09ef9541162b05920a04f645bd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723039"
---
# <a name="bpreqifields"></a>BPREQI_FIELDS
Especifica as informações a serem recuperados sobre uma solicitação de ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
typedef DWORD BPREQI_FIELDS;
```

```csharp
public enum enum_BPREQI_FIELDS {
    BPREQI_BPLOCATION   = 0x0001,
    BPREQI_LANGUAGE     = 0x0002,
    BPREQI_PROGRAM      = 0x0004,
    BPREQI_PROGRAMNAME  = 0x0008,
    BPREQI_THREAD       = 0x0010,
    BPREQI_THREADNAME   = 0x0020,
    BPREQI_PASSCOUNT    = 0x0040,
    BPREQI_CONDITION    = 0x0080,
    BPREQI_FLAGS        = 0x0100,
    BPREQI_ALLOLDFIELDS = 0x01ff
    BPREQI_VENDOR       = 0x0200,   // BP_REQUEST_INFO2 only
    BPREQI_CONSTRAINT   = 0x0400,   // BP_REQUEST_INFO2 only
    BPREQI_TRACEPOINT   = 0x0800,   // BP_REQUEST_INFO2 only
    BPREQI_ALLFIELDS    = 0x0fff    // BP_REQUEST_INFO2 only
};
```

## <a name="members"></a>Membros
BPREQI_BPLOCATION Initialize/usar o `bpLocation` campo (localização do ponto de interrupção) a [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) estrutura.

BPREQI_LANGUAGE Initialize/usar o `guidLanguage` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_PROGRAM Initialize/usar o `pProgram` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_PROGRAMNAME Initialize/usar o `bstrProgramName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_THREAD Initialize/usar o `pThread` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_THREADNAME Initialize/usar o `bstrThreadName` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_PASSCOUNT Initialize/usar o `bpPassCount` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_CONDITION Initialize/usar o `bpCondition` campo (condição de ponto de interrupção) da `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

BPREQI_FLAGS Initialize/usar o `dwFlags` campo do `BP_REQUEST_INFO` ou `BP_REQUEST_INFO2` estrutura.

Inicializar BPREQI_ALLOLDFIELDS/usar todos os campos para o do `BP_REQUEST_INFO` estrutura.

BPREQI_VENDOR Initialize/usar o `guidVendor` campo de `BP_REQUEST_INFO2` estrutura.

BPREQI_CONSTRAINT Initialize/usar o `bstrConstraint` campo de `BP_REQUEST_INFO2` estrutura.

BPREQI_TRACEPOINT Initialize/usar o `bstrTracepoint` campo de `BP_REQUEST_INFO2` estrutura.

BPREQI_ALLFIELDS especifica todos os campos para o `BP_REQUEST_INFO2` estrutura.

## <a name="remarks"></a>Comentários
Passado como um argumento para o [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) métodos para especificar quais campos dos [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2 ](../../../extensibility/debugger/reference/bp-request-info2.md) estruturas são a ser inicializado.

Esses sinalizadores também são usados para indicar quais campos do `BP_REQUEST_INFO` e `BP_REQUEST_INFO2` estruturas são usadas e é válido quando cada estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
