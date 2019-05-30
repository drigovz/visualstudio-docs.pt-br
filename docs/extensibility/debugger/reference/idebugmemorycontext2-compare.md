---
title: IDebugMemoryContext2::Compare | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Compare
helpviewer_keywords:
- IDebugMemoryContext2::Compare method
- Compare method
ms.assetid: c51b5128-848e-4d8e-b2e9-1161339763c3
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9994f99759d570780729fe1c62e6604786e4eb90
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347038"
---
# <a name="idebugmemorycontext2compare"></a>IDebugMemoryContext2::Compare
Compara o contexto de memória para cada contexto na matriz fornecida da maneira indicada por sinalizadores de comparação, retornando um índice do primeiro contexto que corresponde ao.

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

## <a name="parameters"></a>Parâmetros
`compare`\
[in] Um valor a partir de [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md) enumeração que determina o tipo de comparação.

`rgpMemoryContextSet`\
[in] Uma matriz de referências para o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objetos a ser comparada.

`dwMemoryContextSetLen`\
[in] O número de contextos no `rgpMemoryContextSet` matriz.

`pdwMemoryContext`\
[out] Retorna o índice do primeiro contexto de memória que satisfaz a comparação.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_COMPARE_CANNOT_COMPARE` se os dois contextos não podem ser comparados.

## <a name="remarks"></a>Comentários
 Um mecanismo de depuração (DES) oferecem suporte a todos os tipos de comparações, mas ele deve suportar pelo menos `CONTEXT_EQUAL`, `CONTEXT_LESS_THAN`, `CONTEXT_GREATER_THAN` e `CONTEXT_SAME_SCOPE`.

## <a name="see-also"></a>Consulte também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
- [CONTEXT_COMPARE](../../../extensibility/debugger/reference/context-compare.md)