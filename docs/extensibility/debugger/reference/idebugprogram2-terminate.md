---
title: IDebugProgram2::Terminate | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::Terminate
helpviewer_keywords:
- IDebugProgram2::Terminate
ms.assetid: 4d3127d3-b1e9-4b28-ac22-2f2eea255f86
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 16a6d60173090642bda7d8fd940ecf0699e1d7ec
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66331503"
---
# <a name="idebugprogram2terminate"></a>IDebugProgram2::Terminate
Encerra o programa.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Terminate( 
   void 
);
```

```csharp
int Terminate();
```

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Se possível, o programa será encerrado e descarregado do processo; Caso contrário, o mecanismo de depuração (DES) executará qualquer limpeza necessária.

 Esse método ou o [Terminate](../../../extensibility/debugger/reference/idebugprocess2-terminate.md) método é chamado pelo IDE, geralmente em resposta ao usuário interrompendo a depuração de todos os. A implementação desse método Idealmente, deve, encerrar o programa dentro do processo. Se isso não for possível, o DE deve impedir que o programa em execução mais nesse processo (e fazer qualquer limpeza necessária). Se o `IDebugProcess2::Terminate` método foi chamado pelo IDE, todo o processo será encerrado em algum momento depois o `IDebugProgram2::Terminate` método é chamado.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [Terminar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)