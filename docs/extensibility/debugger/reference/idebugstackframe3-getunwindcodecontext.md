---
title: IDebugStackFrame3::GetUnwindCodeContext | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::GetUnwindCodeContext
helpviewer_keywords:
- IDebugStackFrame3::GetUnwindCodeContext method
ms.assetid: b25f7e7d-2b24-48e4-93b3-829e61d73ebf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 488f675c39bb01c87aca13a9bef8cc4a715ecf18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719502"
---
# <a name="idebugstackframe3getunwindcodecontext"></a>IDebugStackFrame3::GetUnwindCodeContext
Retorna o contexto de código representando um local se uma operação de desenrolar de pilha ocorreu.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetUnwindCodeContext(
   IDebugCodeContext2 **ppCodeContext
);
```

```csharp
int GetUnwindCodeContext(
   out IDebugCodeContext2 ppCodeContext
);
```

## <a name="parameters"></a>parâmetros
`ppCodeContext`\
[fora] Retorna um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que representa o local de contexto de código se uma pilha descontraída ocorreu.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Embora este método possa retornar um contexto de código para o local após uma pilha descontrair, isso não significa necessariamente que o desenrolar da pilha possa realmente ocorrer no quadro de pilha atual.

## <a name="see-also"></a>Confira também
- [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
