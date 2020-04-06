---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1c88b50644d1adda2dd0eaa3b74a828f9739d70b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737610"
---
# <a name="context_compare"></a>CONTEXT_COMPARE
Especifica os critérios para comparar dois contextos de memória.

## <a name="syntax"></a>Sintaxe

```cpp
enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
typedef DWORD CONTEXT_COMPARE;
```

```csharp
public enum enum_CONTEXT_COMPARE {
    CONTEXT_EQUAL                 = 0x0001,
    CONTEXT_LESS_THAN             = 0x0002,
    CONTEXT_GREATER_THAN          = 0x0003,
    CONTEXT_LESS_THAN_OR_EQUAL    = 0x0004,
    CONTEXT_GREATER_THAN_OR_EQUAL = 0x0005,
    CONTEXT_SAME_SCOPE            = 0x0006,
    CONTEXT_SAME_FUNCTION         = 0x0007,
    CONTEXT_SAME_MODULE           = 0x0008,
    CONTEXT_SAME_PROCESS          = 0x0009
};
```

## <a name="fields"></a>Campos
`CONTEXT_EQUAL`\
Encontre o primeiro contexto de memória na lista que é igual ao contexto de memória de destino.

`CONTEXT_LESS_THAN`\
Encontre o primeiro contexto de memória na lista que é menor do que o contexto de memória de destino.

`CONTEXT_GREATER_THAN`\
Encontre o primeiro contexto de memória na lista que é maior do que o contexto de memória de destino.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Encontre o primeiro contexto de memória na lista que seja menor ou igual ao contexto de memória-alvo.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Encontre o primeiro contexto de memória na lista que seja maior ou igual ao contexto de memória-alvo.

`CONTEXT_SAME_SCOPE`\
Encontre o primeiro contexto de memória na lista que está no mesmo escopo do contexto de memória de destino.

`CONTEXT_SAME_FUNCTION`\
Encontre o primeiro contexto de memória na lista que está na mesma função que o escopo de memória de destino.

`CONTEXT_SAME_MODULE`\
Encontre o primeiro contexto de memória na lista que está no mesmo módulo do contexto de memória de destino.

`CONTEXT_SAME_PROCESS`\
Encontre o primeiro contexto de memória na lista que está no mesmo processo que o contexto de memória de destino.

## <a name="remarks"></a>Comentários
Passou como um argumento para o método [Compare.](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)

Esses valores são usados para encontrar o primeiro contexto de memória em uma lista que satisfaz os critérios de comparação especificados. Um contexto de memória recebe uma lista de contextos de memória para se comparar através do `IDebugMemoryContext2::Compare` método. O primeiro contexto de memória na lista `true` para a qual o operador de comparação é então retornado.

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
