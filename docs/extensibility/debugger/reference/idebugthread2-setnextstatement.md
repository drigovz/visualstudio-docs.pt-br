---
title: 'IDebugThread2:: SetNextStatement | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7c8a7aff8c6e902b20c5569e2553aececae835ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893705"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
Define o ponteiro de instrução atual para o contexto de código fornecido.

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

## <a name="parameters"></a>Parâmetros
`pStackFrame`\
Reservado para uso futuro; Defina como um valor nulo.

`pCodeContext`\
no Um objeto [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) que descreve o local do código a ser executado e seu contexto.

## <a name="return-value"></a>Valor retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A tabela a seguir mostra outros valores possíveis.

|Valor|Descrição|
|-----------|-----------------|
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|A próxima instrução não pode estar em um intervalo de pilha mais profundo na pilha de quadros.|
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|A próxima instrução não está associada a nenhum quadro na pilha.|
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Alguns mecanismos de depuração não podem definir a próxima instrução após uma exceção.|

## <a name="remarks"></a>Comentários
 O ponteiro de instrução indica a próxima instrução ou instrução a ser executada. Esse método é usado para repetir uma linha de código-fonte ou para forçar a execução a continuar em outra função, por exemplo.

## <a name="see-also"></a>Confira também
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
