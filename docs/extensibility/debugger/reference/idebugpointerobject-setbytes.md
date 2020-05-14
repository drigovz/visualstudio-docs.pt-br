---
title: IDebugPointerObject::SetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::SetBytes
helpviewer_keywords:
- IDebugPointerObject::SetBytes method
ms.assetid: 8c578b38-38d7-46f3-bb2e-8a730fccd334
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dede3ee5291afbfbeab4d6e60dcbd56e205e4526
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725505"
---
# <a name="idebugpointerobjectsetbytes"></a>IDebugPointerObject::SetBytes
Define o valor apontado para uma série de bytes consecutivos.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetBytes( 
   DWORD  dwStart,
   DWORD  dwCount,
   BYTE*  pBytes,
   DWORD* pdwBytes
);
```

```csharp
int SetBytes(
   uint     dwStart,
   uint     dwCount,
   byte[]   pBytes,
   out uint pdwBytes
);
```

## <a name="parameters"></a>parâmetros
`dwStart`\
[em] Um deslocamento, em bytes, desde o início do objeto apontado para.

`dwCount`\
[em] O número de bytes a definir.

`pBytes`\
[em] Uma matriz de bytes representando o novo valor. Este valor é armazenado no objeto, começando pelo deslocamento dado.

`pdwBytes`\
[fora] Retorna o número de bytes realmente definido.

## <a name="return-value"></a>Valor retornado
 Se for bem sucedido, retorna S_OK; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é usado se o ponteiro representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) apontar para um tipo primitivo ou uma matriz simples de tipos primitivos (ou seja, uma matriz que pode ser representada por uma simples seqüência de bytes). Este `IDebugPointerObject` objeto não pode ser uma referência nula (ele deve apontar para um endereço na memória).

## <a name="see-also"></a>Confira também
- [GetBytes](../../../extensibility/debugger/reference/idebugpointerobject-getbytes.md)
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
