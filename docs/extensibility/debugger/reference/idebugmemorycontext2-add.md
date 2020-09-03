---
title: 'IDebugMemoryContext2:: Add | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
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

## <a name="parameters"></a>Parâmetros
`dwCount`\
no O valor a ser adicionado ao contexto atual.

`ppMemCxt`\
fora Retorna um novo objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um contexto de memória é um endereço, portanto, a adição de um valor a um endereço produz um novo endereço que requer uma nova interface de contexto.

 Esse método sempre deve produzir um novo contexto, mesmo se o endereço resultante estiver fora do espaço de memória associado a esse contexto. A única exceção a isso é se nenhuma memória puder ser alocada para o novo contexto ou se `ppMemCxt` for um valor nulo (que é um erro).

## <a name="see-also"></a>Confira também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
