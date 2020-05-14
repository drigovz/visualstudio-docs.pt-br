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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a21fa2ec6d48bb1d6bf17bbc0d2ebf0d90a25a9f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727474"
---
# <a name="idebugmemorycontext2add"></a>IDebugMemoryContext2::Add
Adiciona o valor especificado ao contexto atual e retorna um novo contexto.

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

## <a name="parameters"></a>parâmetros
`dwCount`\
[em] O valor a ser adicionado ao contexto atual.

`ppMemCxt`\
[fora] Retorna um novo objeto [IDebugMemoryContext2.](../../../extensibility/debugger/reference/idebugmemorycontext2.md)

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um contexto de memória é um endereço, então adicionar um valor a um endereço produz um novo endereço que requer uma nova interface de contexto.

 Esse método deve sempre produzir um novo contexto, mesmo que o endereço resultante esteja fora do espaço de memória associado a esse contexto. A única exceção a isso é se nenhuma memória `ppMemCxt` pode ser alocada para o novo contexto ou se for um valor nulo (o que é um erro).

## <a name="see-also"></a>Confira também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
