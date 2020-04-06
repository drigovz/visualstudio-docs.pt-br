---
title: IDebugMemoryBytes2::ReadAt | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::ReadAt
helpviewer_keywords:
- IDebugMemoryBytes2::ReadAt method
- ReadAt method
ms.assetid: b413684d-4155-4bd4-ae30-ffa512243b5f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f909ac3d2e2993879e4c24140abbf23c2ee8d545
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727539"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lê uma seqüência de bytes, começando em um determinado local.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ReadAt( 
   IDebugMemoryContext2* pStartContext,
   DWORD                 dwCount,
   BYTE*                 rgbMemory,
   DWORD*                pdwRead,
   DWORD*                pdwUnreadable
);
```

```csharp
int ReadAt(
   IDebugMemoryContext2 pStartContext,
   uint                 dwCount,
   byte[]               rgbMemory,
   out uint             pdwRead,
   ref uint             pdwUnreadable
);
```

## <a name="parameters"></a>parâmetros
`pStartContext`\
[em] O objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica por onde começar a ler bytes.

`dwCount`\
[em] O número de bytes para ler. Também especifica o comprimento `rgbMemory` da matriz.

`rgbMemory`\
[dentro, fora] Matriz preenchida com os bytes realmente lidos.

`pdwRead`\
[fora] Retorna o número de bytes contíguos realmente lidos.

`pdwUnreadable`\
[dentro, fora] Retorna o número de bytes ilegíveis. Pode ser um valor nulo se o cliente não estiver interessado no número de bytes ilegíveis.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se 100 bytes forem solicitados e os primeiros 50 forem legíveis, os próximos 20 são ilegíveis e os 30 restantes são legíveis, este método retorna:

 *`pdwRead`= 50

 *`pdwUnreadable`= 20

 Neste caso, `*pdwRead + *pdwUnreadable < dwCount`porque, o chamador deve fazer uma chamada adicional para ler os 30 bytes restantes dos 100 originais solicitados e o objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passado no `pStartContext` parâmetro deve ser avançado em 70.

## <a name="see-also"></a>Confira também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
