---
title: 'IDebugStackFrame2:: GetPhysicalStackRange | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
helpviewer_keywords:
- IDebugStackFrame2::GetPhysicalStackRange
ms.assetid: 2f6992e2-ac1c-433f-83b7-a7f83a4ce63d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8c4c4bbc468403aaf94aca1b5133a732e0c050b2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837470"
---
# <a name="idebugstackframe2getphysicalstackrange"></a>IDebugStackFrame2::GetPhysicalStackRange
Obtém uma representação dependente de computador do intervalo de endereços físicos associados a um quadro de pilha.

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
fora Retorna o endereço físico mais baixo associado a esse quadro de pilha.

`paddrMax`\
fora Retorna o endereço físico mais alto associado a esse quadro de pilhas.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 As informações retornadas por esse método são usadas pelo SDM (Gerenciador de depuração de sessão) para classificar os quadros de pilha.

 Supõe-se que a pilha de chamadas cresce, ou seja, que novos quadros de pilha são adicionados em endereços de memória cada vez mais baixos. Uma arquitetura de tempo de execução deve fornecer intervalos de pilha física que correspondam a essa suposição.

## <a name="see-also"></a>Consulte também
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
