---
title: CONTEXT_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_INFO_FIELDS
helpviewer_keywords:
- CONTEXT_INFO_FIELDS enumeration
ms.assetid: ef436bd3-738e-47e8-828c-8febce752439
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b398e7ee549026750cbdff7b7fede8522116f346
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737596"
---
# <a name="context_info_fields"></a>CONTEXT_INFO_FIELDS
Especifica quais informações recuperar sobre um contexto de memória.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
typedef DWORD CONTEXT_INFO_FIELDS;
```

```csharp
public enum enum_CONTEXT_INFO_FIELDS {
    CIF_MODULEURL =       0x00000001,
    CIF_FUNCTION =        0x00000002,
    CIF_FUNCTIONOFFSET =  0x00000004,
    CIF_ADDRESS =         0x00000008,
    CIF_ADDRESSOFFSET =   0x00000010,
    CIF_ADDRESSABSOLUTE = 0x00000020,
    CIF_ALLFIELDS =       0x0000003f
};
```

## <a name="fields"></a>Campos
`CIF_MODULEURL`\
Inicializar/utilizar `bstrModuleUrl` o campo da estrutura [CONTEXT_INFO.](../../../extensibility/debugger/reference/context-info.md)

`CIF_FUNCTION`\
Inicializar/utilizar `bstrFunction` o campo `CONTEXT_INFO` da estrutura.

`CIF_FUNCTIONOFFSET`\
Inicializar/utilizar `posFunctionOffset` o campo `CONTEXT_INFO` da estrutura.

`CIF_ADDRESS`\
Inicializar/utilizar `bstrAddress` o campo `CONTEXT_INFO` da estrutura.

`CIF_ADDRESSOFFSET`\
Inicializar/utilizar `bstrAddressOffset` o campo `CONTEXT_INFO` da estrutura.

`CIF_ALLFIELDS`\
Inicializar/utilizar todos os `CONTEXT_INFO` campos da estrutura.

## <a name="remarks"></a>Comentários
Esses valores são passados um parâmetro para o método [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) para indicar quais campos da estrutura [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) devem ser inicializados.

Essas bandeiras também são usadas `CONTEXT_INFO` para indicar quais campos da estrutura são usados e válidos quando a estrutura é devolvida.

Esses valores podem ser combinados com um pouco de OR.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)
