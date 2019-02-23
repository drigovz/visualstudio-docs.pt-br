---
title: MODULE_FLAGS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_FLAGS
helpviewer_keywords:
- MODULE_FLAGS enumeration
ms.assetid: 0e555b42-b846-4dbb-812e-8e3d11c85b2d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3ec96c5ba806e6eff735edc8093868b19ebaf5b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681394"
---
# <a name="moduleflags"></a>MODULE_FLAGS
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

## <a name="members"></a>Membros
 MODULE_FLAG_NONE não especifica nenhum módulo.

 MODULE_FLAG_SYSTEM Especifica um módulo do sistema.

 MODULE_FLAG_SYMBOLS Especifica um módulo de símbolo.

 MODULE_FLAG_64BIT Especifica um módulo de 64 bits.

 MODULE_FLAG_OPTIMIZED Especifica que o módulo foi otimizado. Esse estado é refletido na **módulos** janela.

 MODULE_FLAG_UNOPTIMIZED Especifica que o módulo não foi otimizado. Esse estado é refletido na **módulos** janela. Isso é o estado padrão.

## <a name="remarks"></a>Comentários
 Usado para o `m_dwModuleFlags` membro a [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) estrutura.

 Esses sinalizadores podem ser combinados com um bit a bit `OR`.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)