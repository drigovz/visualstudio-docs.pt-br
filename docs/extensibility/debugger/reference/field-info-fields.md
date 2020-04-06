---
title: FIELD_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- FIELD_INFO_FIELDS
helpviewer_keywords:
- FIELD_INFO_FIELDS enumeration
ms.assetid: a69487d2-e701-4165-804a-8a011df9a3bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9a3d2e796d37606c51918d8e49db920161d63f55
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736899"
---
# <a name="field_info_fields"></a>FIELD_INFO_FIELDS
Especifica quais informações recuperar sobre um objeto [IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

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

## <a name="fields"></a>Campos
`FIF_FULLNAME`\
Inicializar/utilizar `bstrFullName` o campo na estrutura [FIELD_INFO.](../../../extensibility/debugger/reference/field-info.md)

`FIF_NAME`\
Inicializar/usar `bstrName` o campo `FIELD_INFO` na estrutura.

`FIF_TYPE`\
Inicializar/usar `bstrType` o campo `FIELD_INFO` na estrutura.

`FIF_MODIFIERS`\
Inicializar/usar `bstrModifiers` o campo `FIELD_INFO` na estrutura.

## <a name="remarks"></a>Comentários
Esses valores também são passados como um argumento para o método [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) para especificar quais campos da estrutura [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) devem ser inicializados.

Esses valores também `dwFields` são utilizados no membro da `FIELD_INFO` estrutura para indicar quais campos são usados e válidos.

Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
Cabeçalho: sh.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)
