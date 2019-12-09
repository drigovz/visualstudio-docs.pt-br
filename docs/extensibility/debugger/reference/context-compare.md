---
title: CONTEXT_COMPARE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONTEXT_COMPARE
helpviewer_keywords:
- CONTEXT_COMPARE enumeration
ms.assetid: 701ed61c-a320-4c20-a335-0b840024abc0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28e81e8247e0ab7a7b2e972209805c8bcff053a7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346395"
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

## <a name="fields"></a>Campos
`CONTEXT_EQUAL`\
Localize o contexto de memória primeiro na lista que é igual ao contexto de memória de destino.

`CONTEXT_LESS_THAN`\
Localize o contexto de memória primeiro na lista que é menor que o contexto de memória de destino.

`CONTEXT_GREATER_THAN`\
Localize o contexto de memória primeiro na lista que é maior que o contexto de memória de destino.

`CONTEXT_LESS_THAN_OR_EQUAL`\
Localize o contexto de memória primeiro na lista que é menor ou igual ao contexto de memória de destino.

`CONTEXT_GREATER_THAN_OR_EQUAL`\
Localize o contexto de memória primeiro na lista que é maior que ou igual ao contexto de memória de destino.

`CONTEXT_SAME_SCOPE`\
Localize o contexto de memória primeiro na lista que está no mesmo escopo que o contexto de memória de destino.

`CONTEXT_SAME_FUNCTION`\
Localize o contexto de memória primeiro na lista que está na mesma função que o escopo de memória de destino.

`CONTEXT_SAME_MODULE`\
Localize o contexto de memória primeiro na lista que está no mesmo módulo como o contexto de memória de destino.

`CONTEXT_SAME_PROCESS`\
Localize o contexto de memória primeiro na lista que está no mesmo processo que o contexto de memória de destino.

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
