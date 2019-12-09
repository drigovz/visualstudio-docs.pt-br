---
title: IDebugStackFrame2::GetPhysicalStackRange | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2cf0db9fa776116f1536ae137444160385a8b6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347709"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtém uma representação depende do computador do intervalo de endereços físicos associados a um quadro de pilha.

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

## <a name="parameters"></a>Parâmetros
`paddrMin`\
[out] Retorna o endereço físico mais baixo associado deste quadro de pilhas.

`paddrMax`\
[out] Retorna o endereço físico mais alto associado deste quadro de pilhas.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As informações retornadas por esse método são usadas pelo Gerenciador de depuração de sessão (SDM) para classificar os registros de ativação.

 Supõe-se que a pilha de chamadas cresce para baixo, ou seja, para que novos registros de ativação são adicionados a cada vez mais inferiores endereços de memória. Uma arquitetura de tempo de execução deve fornecer os intervalos de pilha física que correspondem a essa suposição.

## <a name="see-also"></a>Consulte também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)