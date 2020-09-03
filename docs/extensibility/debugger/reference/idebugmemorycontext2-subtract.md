---
title: 'IDebugMemoryContext2:: subtrair | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryContext2::Subtract
helpviewer_keywords:
- Subtract method
- IDebugMemoryContext2::Subtract method
ms.assetid: 63df14c7-8d7e-47c1-afa7-5a1ab5d8eaba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c858beb8c3f9f587633dbae8b3b1fe73fd789663
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727441"
---
# <a name="idebugmemorycontext2subtract"></a>IDebugMemoryContext2::Subtract
Subtrai o valor especificado do contexto atual e retorna um novo contexto.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Subtract( 
   UINT64                 dwCount,
   IDebugMemoryContext2** ppMemCxt
);
```

```csharp
int Subtract(
   ulong                    dwCount,
   out IDebugMemoryContext2 ppMemCxt
);
```

## <a name="parameters"></a>Parâmetros
`dwCount`\
no O número de bytes de memória a serem reduzidos.

`ppMemCxt`\
fora Retorna um novo objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) .

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Um contexto de memória é um endereço, portanto, subtrair um valor de um endereço produz um novo endereço que requer uma nova interface de contexto.

 Esse método sempre deve produzir um novo contexto, mesmo se o endereço resultante estiver fora do espaço de memória associado a esse contexto. A única exceção a isso é se nenhuma memória puder ser alocada para o novo contexto ou se `ppMemCxt` for um valor nulo (que é um erro).

## <a name="see-also"></a>Confira também
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
