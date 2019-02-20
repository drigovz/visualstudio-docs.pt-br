---
title: DUMPTYPE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DUMPTYPE
helpviewer_keywords:
- DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c81d9c9f3f5dc6b0a849e405133b7ecef1e4e59b
ms.sourcegitcommit: 7153e2fc717d32e0e9c8a9b8c406dc4053c9fd53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2019
ms.locfileid: "56412962"
---
# <a name="dumptype"></a>DUMPTYPE
Especifica a quantidade de estado de um programa (como threads em execução, quadros de pilha e o endereço da instrução atual) para despejo.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
typedef DWORD DUMPTYPE;
```

```csharp
public enum enum_DUMPTYPE {
    DUMP_MINIDUMP = 0,
    DUMP_FULLDUMP = 1
};
```

## <a name="members"></a>Membros
DUMP_MINIDUMP  
Especifica um despejo de pequeno e compacto.

DUMP_FULLDUMP  
Especifica um despejo completo, grande.

## <a name="remarks"></a>Comentários
Passado como um argumento para o [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) método.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
[Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)
