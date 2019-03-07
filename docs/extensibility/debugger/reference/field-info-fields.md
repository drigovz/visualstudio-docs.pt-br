---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9614d3b99df71c9bfa8328478348385472f1a8fa
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710000"
---
# <a name="fieldinfofields"></a>FIELD_INFO_FIELDS
Especifica quais informações devem ser recuperadas sobre um [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_FIELD_INFO_FIELDS { 
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
typedef DWORD FIELD_INFO_FIELDS;
```

```csharp
public enum enum_FIELD_INFO_FIELDS {
    FIF_FULLNAME  = 0x0001,
    FIF_NAME      = 0x0002,
    FIF_TYPE      = 0x0004,
    FIF_MODIFIERS = 0x0008,
    FIF_ALL       = 0xffffffff,
    FIF_NONE      = 0x0000
};
```

## <a name="members"></a>Membros
FIF_FULLNAME Initialize/usar o `bstrFullName` campo de [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) estrutura.

FIF_NAME Initialize/usar o `bstrName` campo o `FIELD_INFO` estrutura.

FIF_TYPE Initialize/usar o `bstrType` campo o `FIELD_INFO` estrutura.

FIF_MODIFIERS Initialize/usar o `bstrModifiers` campo o `FIELD_INFO` estrutura.

## <a name="remarks"></a>Comentários
Esses valores também são passados como um argumento para o [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método para especificar quais campos da [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) são de estrutura a ser inicializado.

Esses valores também são usados na `dwFields` membro o `FIELD_INFO` estrutura para indicar quais campos são usados e válido.

Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
