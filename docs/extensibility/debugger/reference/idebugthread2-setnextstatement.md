---
title: IDebugThread2::SetNextStatement | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4b390e5c021fa069ae3fb09eef1978caaf9cc8ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718657"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Define o ponteiro de instrução atual para o contexto de código dado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetNextStatement ( 
   IDebugStackFrame2*  pStackFrame,
   IDebugCodeContext2* pCodeContext
);
```

```csharp
int SetNextStatement ( 
   IDebugStackFrame2  pStackFrame,
   IDebugCodeContext2 pCodeContext
);
```

## <a name="parameters"></a>parâmetros
`pStackFrame`\
Reservado para uso futuro; definido para um valor nulo.

`pCodeContext`\
[em] Um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que descreve o local de código prestes a ser executado e seu contexto.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. A tabela a seguir mostra outros valores possíveis.

|Valor|Descrição|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|A próxima declaração não pode estar em um quadro de pilha mais profundo na pilha de quadros.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|A próxima declaração não está associada a nenhum quadro na pilha.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Alguns mecanismos de depuração não podem definir a próxima declaração após uma exceção.|

## <a name="remarks"></a>Comentários
 O ponteiro de instrução indica a próxima instrução ou instrução a ser executada. Este método é usado para tentar novamente uma linha de código fonte ou para forçar a execução a continuar em outra função, por exemplo.

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
