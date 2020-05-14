---
title: IDebugMemoryContext2:Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b2551f8554d96186b90a1eed97a5a48ec5f0405
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727495"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara o contexto de memória com cada contexto da dada matriz da maneira indicada pela comparação de bandeiras, retornando um índice do primeiro contexto que corresponde.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Compare( 
   CONTEXT_COMPARE        compare,
   IDebugMemoryContext2** rgpMemoryContextSet,
   DWORD                  dwMemoryContextSetLen,
   DWORD*                 pdwMemoryContext
);
```

```csharp
int Compare(
   enum_CONTEXT_COMPARE   compare,
   IDebugMemoryContext2[] rgpMemoryContextSet,
   uint                   dwMemoryContextSetLen,
   out uint               pdwMemoryContext
);
```

## <a name="parameters"></a>parâmetros
`compare`\
[em] Um valor da [enumeração CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) que determina o tipo de comparação.

`rgpMemoryContextSet`\
[em] Uma matriz de referências aos objetos [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) para comparar.

`dwMemoryContextSetLen`\
[em] O número de contextos na `rgpMemoryContextSet` matriz.

`pdwMemoryContext`\
[fora] Retorna o índice do primeiro contexto de memória que satisfaz a comparação.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_COMPARE_CANNOT_COMPARE` se os dois contextos não puderem ser comparados.

## <a name="remarks"></a>Comentários
 Um motor de depuração (DE) não precisa suportar todos os `CONTEXT_EQUAL`tipos `CONTEXT_LESS_THAN` `CONTEXT_GREATER_THAN` de `CONTEXT_SAME_SCOPE`comparações, mas deve suportar pelo menos , e .

## <a name="see-also"></a>Confira também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)
