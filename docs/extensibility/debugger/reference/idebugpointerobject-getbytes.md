---
title: IDebugPointerObject::GetBytes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::GetBytes
helpviewer_keywords:
- IDebugPointerObject::GetBytes method
ms.assetid: e986c188-87fb-4b51-86e9-ee6a0035bdab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d108613c7a557c189a2c42880a5618b42e0bd3b8
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209397"
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

## <a name="parameters"></a>Parâmetros
`dwStart`\
[in] Um deslocamento, em bytes, desde o início do objeto apontado.

`dwCount`\
[in] O número de bytes a serem recuperados.

`pBytes`\
[no, out] Uma matriz que é preenchida com o valor como uma série de bytes consecutivos, começando no deslocamento especificado do objeto apontado.

`pdwBytes`\
[out] Retorna o número de bytes realmente recuperados.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará S_OK; Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Esse método é usado se o ponteiro, conforme representado por este [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) aponta para um tipo primitivo ou uma matriz de tipos primitivos (ou seja, uma matriz que pode ser representado por uma simple sequência de bytes).

## <a name="see-also"></a>Consulte também
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
- [SetBytes](../../../extensibility/debugger/reference/idebugpointerobject-setbytes.md)