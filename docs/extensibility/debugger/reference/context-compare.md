---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21628bda9dc0437672b0b755bb64f1c882b0acbf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689168"
---
# <a name="contextcompare"></a>CONTEXT_COMPARE
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

## <a name="members"></a>Membros
CONTEXT_EQUAL encontrar o contexto de memória primeiro na lista que é igual ao contexto de memória de destino.

CONTEXT_LESS_THAN encontrar o contexto de memória primeiro na lista que é menor que o contexto de memória de destino.

CONTEXT_GREATER_THAN encontrar o contexto de memória primeiro na lista que é maior que o contexto de memória de destino.

CONTEXT_LESS_THAN_OR_EQUAL encontrar o contexto de memória primeiro na lista que é menor que ou igual ao contexto de memória de destino.

CONTEXT_GREATER_THAN_OR_EQUAL encontrar o contexto de memória primeiro na lista que é maior que ou igual ao contexto de memória de destino.

CONTEXT_SAME_SCOPE encontrar o contexto de memória primeiro na lista que está no mesmo escopo que o contexto de memória de destino.

CONTEXT_SAME_FUNCTION encontrar o contexto de memória primeiro na lista que está na mesma função que o escopo de memória de destino.

CONTEXT_SAME_MODULE encontrar o contexto de memória primeiro na lista que está no mesmo módulo como o contexto de memória de destino.

CONTEXT_SAME_PROCESS encontrar o contexto de memória primeiro na lista que está no mesmo processo que o contexto de memória de destino.

## <a name="remarks"></a>Comentários
Passado como um argumento para o [comparar](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md) método.

Esses valores são usados para localizar o contexto de memória primeiro em uma lista que satisfaz os critérios de comparação especificado. Um contexto de memória é dada uma lista de contextos de memória para comparar a próprio em relação a por meio de `IDebugMemoryContext2::Compare` método. O contexto de memória primeiro na lista para o qual o operador de comparação é `true` , em seguida, será retornado.

## <a name="requirements"></a>Requisitos
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Enumerações](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Compare](../../../extensibility/debugger/reference/idebugmemorycontext2-compare.md)
