---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78c7f24d64ffca667706c3b2fcebeffad16a9d85
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714263"
---
# <a name="module_flags"></a>MODULE_FLAGS
Usado para descrever um módulo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
typedef DWORD MODULE_FLAGS;
```

```csharp
public enum enum_MODULE_FLAGS { 
   MODULE_FLAG_NONE        = 0x0000,
   MODULE_FLAG_SYSTEM      = 0x0001,
   MODULE_FLAG_SYMBOLS     = 0x0002,
   MODULE_FLAG_64BIT       = 0x0004,
   MODULE_FLAG_OPTIMIZED   = 0x0008,
   MODULE_FLAG_UNOPTIMIZED = 0x0010
};
```

## <a name="fields"></a>Campos
 `MODULE_FLAG_NONE`\
 Não especifica nenhum módulo.

 `MODULE_FLAG_SYSTEM`\
 Especifica um módulo de sistema.

 `MODULE_FLAG_SYMBOLS`\
 Especifica um módulo de símbolo.

 `MODULE_FLAG_64BIT`\
 Especifica um módulo de 64 bits.

 `MODULE_FLAG_OPTIMIZED`\
 Especifica que o módulo foi otimizado. Este estado é refletido na janela **Módulos.**

 `MODULE_FLAG_UNOPTIMIZED`\
 Especifica que o módulo não foi otimizado. Este estado é refletido na janela **Módulos.** Esse é o valor padrão.

## <a name="remarks"></a>Comentários
 Usado para `m_dwModuleFlags` o membro da estrutura [MODULE_INFO.](../../../extensibility/debugger/reference/module-info.md)

 Essas bandeiras podem ser combinadas com um pouco `OR`.

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
