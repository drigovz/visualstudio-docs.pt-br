---
title: BPRESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPRESI_FIELDS
helpviewer_keywords:
- BPRESI_FIELDS enumeration
ms.assetid: 99f17b1e-3e67-4f85-89d6-5c6cf45c8008
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 82a286bea92c778ab150cacdc80d79f8ac283469
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66350481"
---
# <a name="bpresifields"></a>BPRESI_FIELDS
Especifica as informações a serem recuperados sobre a resolução bem-sucedida de um ponto de interrupção.

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
Inicialização/usar o `bpResLocation` campo (localização de resolução de ponto de interrupção) a [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) estrutura.

`BPRESI_PROGRAM`\
Inicialização/usar o `pProgram` campo do `BP_RESOLUTION_INFO` estrutura.

`BPRESI_THREAD`\
Inicialização/usar o `pThread` campo do `BP_RESOLUTION_INFO` estrutura.

`BPRESI_ALLFIELDS`\
Especifica todos os campos.

## <a name="remarks"></a>Comentários
Passado para o [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) método para indicar quais campos da [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) são de estrutura a ser inicializado.

Esses sinalizadores também são usados para indicar quais campos do `BP_RESOLUTION_INFO` estrutura são usados e válidos quando essa estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
