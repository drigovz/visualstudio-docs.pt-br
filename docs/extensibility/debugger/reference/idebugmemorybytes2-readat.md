---
title: 'IDebugMemoryBytes2:: ReadAt | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 81a6ce40457243e5492d5c6a44dd5d9dd590920f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909935"
---
# <a name="idebugmemorybytes2readat"></a>IDebugMemoryBytes2::ReadAt
Lê uma sequência de bytes, começando em um determinado local.

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

## <a name="parameters"></a>Parâmetros
`pStartContext`\
no O objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica onde começar a ler bytes.

`dwCount`\
no O número de bytes a serem lidos. Também especifica o comprimento da `rgbMemory` matriz.

`rgbMemory`\
[entrada, saída] Matriz preenchida com os bytes realmente lidos.

`pdwRead`\
fora Retorna o número de bytes contíguos realmente lidos.

`pdwUnreadable`\
[entrada, saída] Retorna o número de bytes ilegíveis. Pode ser um valor nulo se o cliente não tiver interesse no número de bytes ilegíveis.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se forem solicitados 100 bytes e o primeiro 50 for legível, os próximos 20 serão ilegíveis e os 30 restantes serão legíveis, esse método retornará:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Nesse caso, como `*pdwRead + *pdwUnreadable < dwCount` , o chamador deve fazer uma chamada adicional para ler os 30 bytes restantes do 100 original solicitado e o objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) passado no `pStartContext` parâmetro deve ser avançado por 70.

## <a name="see-also"></a>Confira também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
