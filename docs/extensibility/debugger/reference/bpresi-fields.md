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
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 837bb7d25ab8dea2b146a98cc65d320b58162685
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737728"
---
# <a name="bpresi_fields"></a>BPRESI_FIELDS
Especifica as informações a serem recuperadas sobre a resolução bem-sucedida de um ponto de ruptura.

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
Inicializar/usar `bpResLocation` o campo (localização de resolução de ponto de ruptura) da estrutura [BP_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-resolution-info.md)

`BPRESI_PROGRAM`\
Inicializar/utilizar `pProgram` o campo `BP_RESOLUTION_INFO` da estrutura.

`BPRESI_THREAD`\
Inicializar/utilizar `pThread` o campo `BP_RESOLUTION_INFO` da estrutura.

`BPRESI_ALLFIELDS`\
Especifica todos os campos.

## <a name="remarks"></a>Comentários
Passado para o método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md) para indicar quais campos da estrutura [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) devem ser inicializados.

Essas bandeiras também são usadas `BP_RESOLUTION_INFO` para indicar quais campos da estrutura são usados e válidos quando essa estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)
