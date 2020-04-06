---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3df924c6c8a4373082d61575e4ad8a7ec3f161d1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719661"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtém uma representação dependente da máquina da gama de endereços físicos associados a um quadro de pilha.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPhysicalStackRange ( 
   UINT64* paddrMin,
   UINT64* paddrMax
);
```

```csharp
int GetPhysicalStackRange ( 
   out ulong paddrMin,
   out ulong paddrMax
);
```

## <a name="parameters"></a>parâmetros
`paddrMin`\
[fora] Retorna o endereço físico mais baixo associado a este quadro de pilha.

`paddrMax`\
[fora] Retorna o endereço físico mais alto associado a este quadro de pilha.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As informações devolvidas por este método são usadas pelo Gerenciador de depuração de sessão (SDM) para classificar quadros de pilha.

 Presume-se que a pilha de chamadas cresce, ou seja, que novos quadros de pilha são adicionados em endereços de memória cada vez mais baixos. Uma arquitetura de tempo de execução deve fornecer intervalos de pilha físicos que correspondam a essa suposição.

## <a name="see-also"></a>Confira também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
