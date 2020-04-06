---
title: IDebugMemoryBytes2:GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::GetSize
helpviewer_keywords:
- IDebugMemoryBytes2::GetSize method
- GetSize method
ms.assetid: dae64c5f-5b54-40c3-b32f-ec3b16c093f7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de4eccb395059112dde40af36ce75798db9064b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727552"
---
# <a name="idebugmemorybytes2getsize"></a>IDebugMemoryBytes2::GetSize
Recupera o tamanho, em bytes, da memória representada por este objeto [IDebugMemoryBytes2.](../../../extensibility/debugger/reference/idebugmemorybytes2.md)

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSize( 
   UINT64* pqwSize
);
```

```csharp
int GetSize(
   out ulong pqwSize
);
```

## <a name="parameters"></a>parâmetros
`pqwSize`\
[fora] Retorna o tamanho, em bytes do espaço de memória.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="see-also"></a>Confira também
- [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)
