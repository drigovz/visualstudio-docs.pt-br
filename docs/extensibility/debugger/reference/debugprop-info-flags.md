---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa7e4a498188dc91f2a47b3ccf27f367f15ec77b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737400"
---
# <a name="debugprop_info_flags"></a>DEBUGPROP_INFO_FLAGS
Especifica quais informações recuperar sobre um objeto de propriedade de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
typedef DWORD DEBUGPROP_INFO_FLAGS;
```

```csharp
public enum enum_DEBUGPROP_INFO_FLAGS {
    DEBUGPROP_INFO_FULLNAME          = 0x00000001,
    DEBUGPROP_INFO_NAME              = 0x00000002,
    DEBUGPROP_INFO_TYPE              = 0x00000004,
    DEBUGPROP_INFO_VALUE             = 0x00000008,
    DEBUGPROP_INFO_ATTRIB            = 0x00000010,
    DEBUGPROP_INFO_PROP              = 0x00000020,
    DEBUGPROP_INFO_VALUE_AUTOEXPAND  = 0x00010000,
    DEBUGPROP_INFO_VALUE_NOFUNCEVAL  = 0x00020000,
    DEBUGPROP_INFO_VALUE_RAW         = 0x00040000,
    DEBUGPROP_INFO_VALUE_NO_TOSTRING = 0x00080000
    DEBUGPROP_INFO_NONE              = 0x00000000,
    DEBUGPROP_INFO_STANDARD          = DEBUGPROP_INFO_ATTRIB |
                                        DEBUGPROP_INFO_NAME |
                                        DEBUGPROP_INFO_TYPE |
                                        DEBUGPROP_INFO_VALUE,
    DEBUGPROP_INFO_ALL               = 0xffffffff
};
```

## <a name="fields"></a>Campos
`DEBUGPROP_INFO_FULLNAME`\
Inicializar/usar `bstrFullName` o campo.

`DEBUGPROP_INFO_NAME`\
Inicializar/usar `bstrName` o campo.

`DEBUGPROP_INFO_TYPE`\
Inicializar/usar `bstrType` o campo.

`DEBUGPROP_INFO_VALUE`\
Inicializar/usar `bstrValue` o campo.

`DEBUGPROP_INFO_ATTRIB`\
Inicializar/usar `dwAttrib` o campo.

`DEBUGPROP_INFO_PROP`\
Inicializar/usar `pProperty` o campo que contém uma interface [IDebugProperty2.](../../../extensibility/debugger/reference/idebugproperty2.md)

`DEBUGPROP_INFO_VALUE_AUTOEXPAND`\
Especifica que o campo de valor deve conter o valor expandido automaticamente, se disponível, para este tipo de objeto.

`DEBUGPROP_INFO_VALUE_NOFUNCEVAL`\
Preterido.

`DEBUGPROP_INFO_VALUE_RAW`\
Não retorne nenhum valor embelezado ou membros (ou seja, não formatar os valores).

`DEBUGPROP_INFO_VALUE_NO_TOSTRING`\
Não retorne nenhum valor especial sintetizado (por exemplo, não chame `ToString()` um objeto para produzir um valor).

`DEBUGPROP_INFO_NONE`\
Especifica que nenhuma bandeira está definida.

`DEBUGPROP_INFO_STANDARD`\
Inicializar/usar `dwAttrib`os `bstrName` `bstrType`campos `bstrValue` e campos.

`DEBUGPROP_INFO_All`\
Indica uma máscara de todas as bandeiras.

## <a name="remarks"></a>Comentários
Esses valores são passados para os métodos [GetPropertyInfo,](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) para indicar quais campos devem ser inicializados na estrutura [DEBUG_PROPERTY_INFO.](../../../extensibility/debugger/reference/debug-property-info.md)

Esses valores também `dwFields` são utilizados para que o `DEBUG_PROPERTY_INFO` membro da estrutura indique quais campos da estrutura são utilizados e válidos quando a estrutura é devolvida.

Esses valores podem ser combinados com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [Getpropertyinfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
