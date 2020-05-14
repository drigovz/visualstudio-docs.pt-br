---
title: IDebugPointerObject::GetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17bc39f65d7c4c42b4f958b559df7c5b7d3bbdf7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725523"
---
# <a name="idebugpointerobjectgetbytes"></a>IDebugPointerObject::GetBytes
Obtém o valor apontado como uma série de bytes consecutivos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int GetBytes(
   uint       dwStart,
   uint       dwCount,
   out byte[] pBytes,
   out uint   pdwBytes
);
```

## <a name="parameters"></a>parâmetros
`dwStart`\
[em] Um deslocamento, em bytes, desde o início do objeto apontado para.

`dwCount`\
[em] O número de bytes para recuperar.

`pBytes`\
[dentro, fora] Uma matriz que é preenchida com o valor como uma série de bytes consecutivos, começando pelo deslocamento dado do objeto apontado para.

`pdwBytes`\
[fora] Retorna o número de bytes realmente recuperado.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é usado se o ponteiro representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apontar para um tipo primitivo ou uma matriz simples de tipos primitivos (ou seja, uma matriz que pode ser representada por uma simples seqüência de bytes).

## <a name="see-also"></a>Confira também
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [Setbytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)
