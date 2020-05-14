---
title: BPERESI_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BPERESI_FIELDS
helpviewer_keywords:
- BPERESI_FIELDS enumeration
ms.assetid: dd7dd89c-1043-46a1-a929-099cc039c344
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: af2f20e7d3abd79261dc18753a7eb940666fc186
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737760"
---
# <a name="bperesi_fields"></a>BPERESI_FIELDS
Especifica as informações a serem recuperadas sobre uma resolução falha de um ponto de ruptura.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
typedef DWORD BPERESI_FIELDS;
```

```csharp
public enum enum_BPERESI_FIELDS {
    PERESI_BPRESLOCATION = 0x0001,
    BPERESI_PROGRAM      = 0x0002,
    BPERESI_THREAD       = 0x0004,
    BPERESI_MESSAGE      = 0x0008,
    BPERESI_TYPE         = 0x0010,
    BPERESI_ALLFIELDS    = 0xffffffff
};
```

## <a name="fields"></a>Campos
`PERESI_BPRESLOCATION`\
Inicializar/usar `bpResLocation` o campo (localização de resolução de ponto de ruptura) da estrutura [BP_ERROR_RESOLUTION_INFO.](../../../extensibility/debugger/reference/bp-error-resolution-info.md)

`BPERESI_PROGRAM`\
Inicializar/utilizar `pProgram` o campo `BP_ERROR_RESOLUTION_INFO` da estrutura.

`BPERESI_THREAD`\
Inicializar/utilizar `pThread` o campo `BP_ERROR_RESOLUTION_INFO` da estrutura.

`BPERESI_MESSAGE`\
Inicializar/utilizar `bstrMessage` o campo `BP_ERROR_RESOLUTION_INFO` da estrutura.

`BPERESI_TYPE`\
Inicializar/usar `dwType` o campo (tipo ponto `BP_ERROR_RESOLUTION_INFO` de ruptura) da estrutura.

`BPERESI_ALLFIELDS`\
Inicializar/utilizar todos os `BP_ERROR_RESOLUTION_INFO` campos da estrutura.

## <a name="remarks"></a>Comentários
Passou como parâmetro para o método [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) para indicar quais campos da estrutura [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) devem ser inicializados.

Esses valores também são usados `BP_ERROR_RESOLUTION_INFO` para indicar quais campos na estrutura são usados e válidos quando essa estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)
- [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)
