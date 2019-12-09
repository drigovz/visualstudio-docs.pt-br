---
title: IDebugDisassemblyStream2::GetSize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2::GetSize
helpviewer_keywords:
- IDebugDisassemblyStream2::GetSize
ms.assetid: 8f512704-12d0-46d2-959a-4f8dffe117b5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cb13ac24aaa542d3111ff3480ac340615226a0a7
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310412"
---
# <a name="idebugdisassemblystream2getsize"></a>IDebugDisassemblyStream2::GetSize
Obtém o tamanho em instruções deste fluxo de desmontagem.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetSize( 
   UINT64* pnSize
);
```

```csharp
int GetSize( 
   out ulong pnSize
);
```

## <a name="parameters"></a>Parâmetros
`pnSize`\
[out] Retorna o tamanho, em instruções.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 O valor retornado desse método pode ser usado para alocar uma matriz de [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) estruturas que é então passado para o [leitura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
- [Ler](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)