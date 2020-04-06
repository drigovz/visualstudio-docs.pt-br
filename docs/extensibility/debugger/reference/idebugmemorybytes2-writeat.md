---
title: IDebugMemoryBytes2::WriteAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac9113424c6cd5cce230774a6e5335ffa4d4ba77
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727522"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Grava o número especificado de bytes de memória, começando pelo endereço especificado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT WriteAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory
);
```

```csharp
int WriteAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory
);
```

## <a name="parameters"></a>parâmetros
`pStartContext`\
[em] O objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica onde começar a escrever bytes.

`dwCount`\
[em] O número de bytes para escrever.

`rgbMemory`\
[em] Os bytes para escrever. Esta matriz é assumida `dwCount` como sendo pelo menos bytes de tamanho.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, `S_FALSE` retorna se nem todos os bytes podem `E_FAIL`ser escritos ou retorna um código de erro (tipicamente ).

## <a name="remarks"></a>Comentários
 Se o endereço inicial não estiver dentro da janela de memória representada por este objeto [IDebugMemoryBytes2,](../../../extensibility/debugger/reference/idebugmemorybytes2.md) não ocorrerá gravação e um código de `E_FAIL` erro será devolvido — mesmo que a quantidade de gravação se sobreponha ao espaço de memória.

## <a name="see-also"></a>Confira também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
