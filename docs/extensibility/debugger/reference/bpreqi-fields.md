---
title: BPREQI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPREQI_FIELDS
helpviewer_keywords:
- BPREQI_FIELDS enumeration
ms.assetid: 679e771e-4a79-484e-af37-f962ef4aa245
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4c0e10b6c253c61a9e68e0cf161201f7d2520ae6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737753"
---
# <a name="bpreqi_fields"></a>BPREQI_FIELDS
Especifica as informações a serem recuperadas sobre uma solicitação de ponto de ruptura.

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

## <a name="fields"></a>Campos
`BPREQI_BPLOCATION`\
Inicializar/usar `bpLocation` o campo (localização de ponto de ruptura) da estrutura [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) ou [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

`BPREQI_LANGUAGE`\
Inicializar/usar `guidLanguage` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_PROGRAM`\
Inicializar/usar `pProgram` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_PROGRAMNAME`\
Inicializar/usar `bstrProgramName` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_THREAD`\
Inicializar/usar `pThread` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_THREADNAME`\
Inicializar/usar `bstrThreadName` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_PASSCOUNT`\
Inicializar/usar `bpPassCount` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_CONDITION`\
Inicializar/usar `bpCondition` o campo (condição de `BP_REQUEST_INFO` `BP_REQUEST_INFO2` ponto de ruptura) da estrutura ou.

`BPREQI_FLAGS`\
Inicializar/usar `dwFlags` o campo `BP_REQUEST_INFO` `BP_REQUEST_INFO2` da ou estrutura.

`BPREQI_ALLOLDFIELDS`\
Inicializar/utilizar todos os campos `BP_REQUEST_INFO` para a estrutura.

`BPREQI_VENDOR`\
Inicializar/usar `guidVendor` o `BP_REQUEST_INFO2` campo de estrutura.

`BPREQI_CONSTRAINT`\
Inicializar/usar `bstrConstraint` o `BP_REQUEST_INFO2` campo de estrutura.

`BPREQI_TRACEPOINT`\
Inicializar/usar `bstrTracepoint` o `BP_REQUEST_INFO2` campo de estrutura.

`BPREQI_ALLFIELDS`\
Especifica todos os `BP_REQUEST_INFO2` campos para a estrutura.

## <a name="remarks"></a>Comentários
Passou como um argumento para os métodos [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) e [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) para especificar quais campos das estruturas [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) devem ser inicializados.

Essas bandeiras também são usadas `BP_REQUEST_INFO` para `BP_REQUEST_INFO2` indicar quais campos e estruturas são usados e válidos quando cada estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
