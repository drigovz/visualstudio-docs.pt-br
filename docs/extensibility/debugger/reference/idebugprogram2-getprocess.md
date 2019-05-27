---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a443d7f17397526ae0f990627314d8feedad48d4
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212574"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Obtenha o que este programa está em execução no processo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Parâmetros
`ppProcess`\
[out] Retorna o [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) interface que representa o processo.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A menos que um mecanismo de depuração (DES) implementa o [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md) interface, a implementação do desse método deve retornar sempre `E_NOTIMPL` porque a DE não pode determinar qual processo está em execução em e, portanto, não é possível atender a uma implementação deste método.

 Implementando o `IDebugEngineLaunch2` interface significa que o DE deve saber como criar um processo; portanto, a implementação do do [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface é capaz de saber a qual processo está executando no.

## <a name="see-also"></a>Consulte também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)