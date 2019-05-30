---
title: IDebugMemoryContext2::Add | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Add
helpviewer_keywords:
- IDebugMemoryContext2::Add method
- Add method
ms.assetid: 3c47e646-ce9e-4dd3-8f1a-6dbd3827d407
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c1cafbf22e51f867948491e2925c085bd387ea84
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347085"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Adiciona o valor especificado para o contexto atual e retorna um novo contexto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Add( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Add(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parâmetros
`dwCount`\
[in] O valor a ser adicionado ao contexto atual.

`ppMemCxt`\
[out] Retorna um novo [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um contexto de memória é um endereço, portanto, a adição de um valor para um endereço produz um novo endereço que requer uma nova interface de contexto.

 Esse método sempre deve produzir um novo contexto, mesmo se o endereço resultante está fora do espaço de memória associado a este contexto. A única exceção a isso é se nenhuma memória pode ser alocada para o novo contexto ou se `ppMemCxt` é um valor nulo (que é um erro).

## <a name="see-also"></a>Consulte também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)