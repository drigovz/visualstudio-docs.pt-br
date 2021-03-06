---
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8ff77985bca8772d92c3b90e7a727c0077137e24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909910"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
Grava o número especificado de bytes de memória, começando no endereço especificado.

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

## <a name="parameters"></a>Parâmetros
`pStartContext`\
no O objeto [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) que especifica onde começar a gravar bytes.

`dwCount`\
no O número de bytes a serem gravados.

`rgbMemory`\
no Os bytes a serem gravados. Presume-se que essa matriz tenha pelo menos `dwCount` bytes de tamanho.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retornará `S_OK` ; caso contrário, retornará `S_FALSE` se nem todos os bytes puderem ser gravados ou retornarem um código de erro (normalmente `E_FAIL` ).

## <a name="remarks"></a>Comentários
 Se o endereço inicial não estiver dentro da janela de memória representada por esse objeto [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , não ocorrerá nenhuma gravação e um código de erro `E_FAIL` será retornado, mesmo que a quantidade a ser gravada se sobreponha no espaço de memória.

## <a name="see-also"></a>Consulte também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
- [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
