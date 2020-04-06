---
title: MODULE_INFO_FIELDS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_INFO_FIELDS
helpviewer_keywords:
- MODULE_INFO_FIELDS enumeration
ms.assetid: 8bed85f4-235f-4192-b58f-5fad7a4d7a78
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fa64147738a916d44b6924f193860f74bd10a855
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714324"
---
# <a name="module_info_fields"></a>MODULE_INFO_FIELDS
Especifica as bandeiras para as informações do módulo de depuração.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
typedef DWORD MODULE_INFO_FIELDS;
```

```csharp
public enum enum_MODULE_INFO_FIELDS { 
   MIF_NONE              = 0x0000,
   MIF_NAME              = 0x0001,
   MIF_URL               = 0x0002,
   MIF_VERSION           = 0x0004,
   MIF_DEBUGMESSAGE      = 0x0008,
   MIF_LOADADDRESS       = 0x0010,
   MIF_PREFFEREDADDRESS  = 0x0020,
   MIF_SIZE              = 0x0040,
   MIF_LOADORDER         = 0x0080,
   MIF_TIMESTAMP         = 0x0100,
   MIF_URLSYMBOLLOCATION = 0x0200,
   MIF_FLAGS             = 0x0400,
   MIF_ALLFIELDS         = 0x07ff
};
```

## <a name="fields"></a>Campos
 `MIF_NONE`\
 Inicializar/usar nenhum dos campos da estrutura.

 `MIF_NAME`\
 Inicializar/utilizar `m_bstrName` o campo na estrutura [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 `MIF_URL`\
 Inicializar/usar `m_bstrUrl` o campo `MODULE_INFO` na estrutura.

 `MIF_VERSION`\
 Inicializar/usar `m_bstrVersion` o campo `MODULE_INFO` na estrutura.

 `MIF_DEBUGMESSAGE`\
 Inicializar/usar `m_bstrDebugMessage` o campo `MODULE_INFO` na estrutura.

 `MIF_LOADADDRESS`\
 Inicializar/usar `m_addrLoadAddress` o campo `MODULE_INFO` na estrutura.

 `MIF_PREFFEREDADDRESS`\
 Inicializar/usar `m_addrPreferredLoadAddress` o campo `MODULE_INFO` na estrutura.

 `MIF_SIZE`\
 Inicializar/usar `m_dwSize` o campo `MODULE_INFO` na estrutura.

 `MIF_LOADORDER`\
 Inicializar/usar `m_dwLoadOrder` o campo `MODULE_INFO` na estrutura.

 `MIF_TIMESTAMP`\
 Inicializar/usar `m_TimeStamp` o campo `MODULE_INFO` na estrutura.

 `MIF_URLSYMBOLLOCATION`\
 Inicializar/usar `m_bstrUrlSymbolLocation` o campo `MODULE_INFO` na estrutura.

 `MIF_FLAGS`\
 Inicializar/usar `m_dwModuleFlags` o campo `MODULE_INFO` na estrutura.

 `MIF_ALLFIELDS`\
 Inicializar/utilizar todos os campos `MODULE_INFO` da estrutura.

## <a name="remarks"></a>Comentários
 Esses valores são passados como um argumento para o método [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) para indicar quais campos da estrutura [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) devem ser inicializados.

 Esses valores também `MODULE_INFO` são utilizados na estrutura para indicar quais campos são usados e válidos.

 Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
- [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)
