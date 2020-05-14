---
title: IDebugProgram2::GetProcess | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722788"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Pegue o processo em que este programa está sendo executado.

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

## <a name="parameters"></a>parâmetros
`ppProcess`\
[fora] Retorna a interface [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) que representa o processo.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 A menos que um mecanismo de depuração (DE) implemente a interface [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) a implementação do DE deste método deve sempre retornar `E_NOTIMPL` porque um DE não pode determinar em qual processo ele está sendo executado e, portanto, não pode satisfazer uma implementação deste método.

 A implementação da `IDebugEngineLaunch2` interface significa que o DE deve saber como criar um processo; portanto, a implementação do DE da interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) é capaz de saber em que processo está sendo executado.

## <a name="see-also"></a>Confira também
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
