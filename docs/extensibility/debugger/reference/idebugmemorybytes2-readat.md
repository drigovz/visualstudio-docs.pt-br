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
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f787ad06b4e7d612007b6448287b5062ae1b0efd
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718229"
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

#### <a name="parameters"></a>Parâmetros
 `pStartContext`

 [in] O [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto que especifica o local iniciar a leitura dos bytes.

 `dwCount`

 [in] O número de bytes a serem lidos. Também especifica o comprimento do `rgbMemory` matriz.

 `rgbMemory`

 [no, out] Matriz preenchido com os bytes realmente lidos.

 `pdwRead`

 [out] Retorna o número de bytes contíguos realmente lidos.

 `pdwUnreadable`

 [no, out] Retorna o número de bytes não pode ser lido. Pode ser um valor nulo se o cliente não se preocupam com o número de bytes não pode ser lido.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Se 100 bytes são solicitados e os primeiros 50 são legíveis, os próximos 20 são ilegíveis e os 30 restantes são legíveis, esse método retorna:

 *`pdwRead` = 50

 *`pdwUnreadable` = 20

 Nesse caso, porque `*pdwRead + *pdwUnreadable < dwCount`, o chamador deve fazer uma chamada adicional para ler os bytes restantes 30 das 100 original solicitada e o [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) objeto passado a `pStartContext` parâmetro deve ser avançado por 70.

## <a name="see-also"></a>Consulte também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)