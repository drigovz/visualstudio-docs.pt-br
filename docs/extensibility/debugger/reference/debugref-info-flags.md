---
title: DEBUGREF_INFO_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DEBUGREF_INFO_FLAGS
helpviewer_keywords:
- DEBUGREF_INFO_FLAGS enumeration
ms.assetid: 1b043327-302a-4f6d-b51d-f94f9d7c7f9d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05d7d953e62703ecb1790ce9da8c71f4e8f0fdba
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412988"
---
# <a name="debugrefinfoflags"></a>DEBUGREF_INFO_FLAGS
Especifica quais informações devem ser recuperadas sobre um objeto de referência de depuração.

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

## <a name="members"></a>Membros
DEBUGREF_INFO_NAME  
Inicialização/usar o `bstrName` campo na estrutura.

DEBUGREF_INFO_TYPE  
Inicialização/usar o `bstrType` campo na estrutura.

DEBUGREF_INFO_VALUE  
Inicialização/usar o `bstrValue` campo na estrutura.

DEBUGREF_INFO_ATTRIB  
Inicialização/usar o `dwAttrib` campo na estrutura.

DEBUGREF_INFO_REFTYPE  
Inicialização/usar o `dwRefType` campo na estrutura.

DEBUGREF_INFO_REF  
Inicialização/usar o `pReference` campo na estrutura.

DEBUGREF_INFO_VALUE_AUTOEXPAND  
O campo de valor deve conter o valor expandida automaticamente, se disponível, para esse tipo de objeto.

DEBUGREF_INFO_NONE  
Indica que nenhum sinalizador está definido.

DEBUGREF_INFO_ALL  
Indica uma máscara dos sinalizadores.

## <a name="remarks"></a>Comentários
Esses sinalizadores são passados para o [EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md) e [GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md) métodos para indicar quais campos dos [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) são de estrutura a ser inicializado.

Usado para o `dwFields` membro o `DEBUG_REFERENCE_INFO` estrutura para indicar quais campos são usados e válidos quando a estrutura é retornada.

Esses valores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
[Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)  
[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)
