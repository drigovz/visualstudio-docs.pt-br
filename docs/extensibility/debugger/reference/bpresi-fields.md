---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0d82650fabf467d44b1bd5eba01599c5cb5e40bb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938257"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Especifica as informações a serem recuperadas sobre a resolução bem-sucedida de um ponto de interrupção.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
typedef DWORD BPRESI_FIELDS;
```

```csharp
public enum enum_BPRESI_FIELDS {
    BPRESI_BPRESLOCATION = 0x0001,
    BPRESI_PROGRAM       = 0x0002,
    BPRESI_THREAD        = 0x0004,
    BPRESI_ALLFIELDS     = 0xffffffff
};
```

## <a name="fields"></a>Campos
`BPRESI_BPRESLOCATION`\
Inicializar/usar o `bpResLocation` campo (local de resolução de ponto de interrupção) da estrutura de [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) .

`BPRESI_PROGRAM`\
Inicializar/usar o `pProgram` campo da `BP_RESOLUTION_INFO` estrutura.

`BPRESI_THREAD`\
Inicializar/usar o `pThread` campo da `BP_RESOLUTION_INFO` estrutura.

`BPRESI_ALLFIELDS`\
Especifica todos os campos.

## <a name="remarks"></a>Comentários
Passado para o método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) para indicar quais campos da estrutura de [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devem ser inicializados.

Esses sinalizadores também são usados para indicar quais campos da `BP_RESOLUTION_INFO` estrutura são usados e válidos quando essa estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR` .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
