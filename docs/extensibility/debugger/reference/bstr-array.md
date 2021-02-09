---
title: BSTR_ARRAY | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BSTR_ARRAY
helpviewer_keywords:
- BSTR_ARRAY structure
ms.assetid: 48da37f7-a237-48a9-9ff9-389c1a00862c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d16eb78cdb6c6b9e665dda8410f46d4cf61ee69a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882206"
---
# <a name="bstr_array"></a>BSTR_ARRAY
Uma estrutura que descreve uma matriz de cadeias de caracteres.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct tagBSTR_ARRAY {
    DWORD dwCount;
    BSTR* Members;
} BSTR_ARRAY;
```

```csharp
struct BSTR_ARRAY {
    DWORD    dwCount;
    string[] Members;
}
```

## <a name="members"></a>Membros
`dwCount`\
Número de cadeias de caracteres na `Members` matriz.

`Members`\
Matriz de cadeias de caracteres.

## <a name="remarks"></a>Comentários
Essa estrutura é retornada do método [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) .

 [Somente C++] Cada cadeia de caracteres individual deve ser liberada usando `SysFreeString` , e a `Members` matriz deve ser liberada com `CoTaskMemFree` .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)
