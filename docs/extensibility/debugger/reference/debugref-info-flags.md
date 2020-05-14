---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb10ae5d3b4ce9f8aa777f643d412e075bd5293f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737381"
---
# <a name="debugref_info_flags"></a>DEBUGREF_INFO_FLAGS
Especifica quais informações recuperar sobre um objeto de referência de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
typedef DWORD DEBUGREF_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGREF_INFO_FLAGS {
    DEBUGREF_INFO_NAME             = 0x00000001,
    DEBUGREF_INFO_TYPE             = 0x00000002,
    DEBUGREF_INFO_VALUE            = 0x00000004,
    DEBUGREF_INFO_ATTRIB           = 0x00000008,
    DEBUGREF_INFO_REFTYPE          = 0x00000010,
    DEBUGREF_INFO_REF              = 0x00000020,
    DEBUGREF_INFO_VALUE_AUTOEXPAND = 0x00010000,
    DEBUGREF_INFO_NONE             = 0x00000000,
    DEBUGREF_INFO_ALL              = 0xffffffff
};
```

## <a name="fields"></a>Campos
`DEBUGREF_INFO_NAME`\
Inicializar/usar `bstrName` o campo na estrutura.

`DEBUGREF_INFO_TYPE`\
Inicializar/usar `bstrType` o campo na estrutura.

`DEBUGREF_INFO_VALUE`\
Inicializar/usar `bstrValue` o campo na estrutura.

`DEBUGREF_INFO_ATTRIB`\
Inicializar/usar `dwAttrib` o campo na estrutura.

`DEBUGREF_INFO_REFTYPE`\
Inicializar/usar `dwRefType` o campo na estrutura.

`DEBUGREF_INFO_REF`\
Inicializar/usar `pReference` o campo na estrutura.

`DEBUGREF_INFO_VALUE_AUTOEXPAND`\
O campo de valor deve conter o valor expandido automaticamente, se disponível, para este tipo de objeto.

`DEBUGREF_INFO_NONE`\
Indica que nenhuma bandeira está definida.

`DEBUGREF_INFO_ALL`\
Indica uma máscara das bandeiras.

## <a name="remarks"></a>Comentários
Essas bandeiras são passadas para os métodos [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) para indicar quais campos da estrutura [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) devem ser inicializados.

Usado para `dwFields` o `DEBUG_REFERENCE_INFO` membro da estrutura para indicar quais campos são usados e válidos quando a estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)
- [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
