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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 41201194ee76f92b4faa101c4811c35b44a0d890
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961879"
---
# <a name="module_flags"></a>MODULE_FLAGS
Usado para descrever um módulo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_MODULE_FLAGS { 
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
public enum enum_MODULE_FLAGS { 
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
 Especifica um módulo do sistema.

 `MODULE_FLAG_SYMBOLS`\
 Especifica um módulo de símbolo.

 `MODULE_FLAG_64BIT`\
 Especifica um módulo de 64 bits.

 `MODULE_FLAG_OPTIMIZED`\
 Especifica que o módulo foi otimizado. Esse estado é refletido na janela **módulos** .

 `MODULE_FLAG_UNOPTIMIZED`\
 Especifica que o módulo não foi otimizado. Esse estado é refletido na janela **módulos** . Esse é o valor padrão.

## <a name="remarks"></a>Comentários
 Usado para o `m_dwModuleFlags` membro da estrutura de [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) .

 Esses sinalizadores podem ser combinados com uma operadora de bits `OR` .

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)
