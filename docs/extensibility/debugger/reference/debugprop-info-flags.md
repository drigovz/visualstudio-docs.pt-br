---
title: DEBUGPROP_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- DEBUGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS enumeration
ms.assetid: 1c7fe777-615e-4929-9ed4-970d9fe0eb81
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 131e014e3714df708c5ef1526ecb911531c5a5c3
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689103"
---
# <a name="debugpropinfoflags"></a>DEBUGPROP_INFO_FLAGS
Especifica quais informações devem ser recuperadas sobre um objeto de propriedade de depuração.

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

## <a name="members"></a>Membros
DEBUGPROP_INFO_FULLNAME Initialize/usar o `bstrFullName` campo.

DEBUGPROP_INFO_NAME Initialize/usar o `bstrName` campo.

DEBUGPROP_INFO_TYPE Initialize/usar o `bstrType` campo.

DEBUGPROP_INFO_VALUE Initialize/usar o `bstrValue` campo.

DEBUGPROP_INFO_ATTRIB Initialize/usar o `dwAttrib` campo.

DEBUGPROP_INFO_PROP Initialize/usar o `pProperty` campo que contém uma [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) interface.

DEBUGPROP_INFO_VALUE_AUTOEXPAND Especifica que o campo de valor deve conter o valor expandida automaticamente, se disponível, para esse tipo de objeto.

DEBUGPROP_INFO_VALUE_NOFUNCEVAL preterido.

DEBUGPROP_INFO_VALUE_RAW não retornam todos os valores beautified ou membros (ou seja, não formatar os valores).

DEBUGPROP_INFO_VALUE_NO_TOSTRING não retornam todos os valores sintetizados especiais (por exemplo, não chame `ToString()` em um objeto para produzir um valor).

DEBUGPROP_INFO_NONE Especifica que nenhum sinalizador está definido.

DEBUGPROP_INFO_STANDARD Initialize/usar o `dwAttrib`, `bstrName`, `bstrType`, e `bstrValue` campos.

DEBUGPROP_INFO_All indica uma máscara de todos os sinalizadores.

## <a name="remarks"></a>Comentários
Esses valores são passados para o [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md), [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md), e [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md) métodos para indicar quais campos devem ser inicializado a [ DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura.

Esses valores também são usados para o `dwFields` membro o `DEBUG_PROPERTY_INFO` estrutura para indicar quais campos da estrutura são usados e válidos quando a estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
- [EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
