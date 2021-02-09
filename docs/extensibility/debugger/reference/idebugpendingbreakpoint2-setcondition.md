---
title: 'IDebugPendingBreakpoint2:: setcondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPendingBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugPendingBreakpoint2::SetCondition method
ms.assetid: 0534224f-654f-4862-bc4d-a9a81a5f8899
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b343b718e393d7a26005fb3587eb9b60527bb0d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897356"
---
# <a name="idebugpendingbreakpoint2setcondition"></a>IDebugPendingBreakpoint2::SetCondition
Define ou altera a condição associada ao ponto de interrupção pendente.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parâmetros
`bpCondition`\
no Uma estrutura de [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que especifica a condição a ser definida.

## <a name="return-value"></a>Valor de retorno
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Qualquer condição que foi associada anteriormente ao ponto de interrupção pendente é perdida. Todos os pontos de interrupção associados a esse ponto de interrupção pendente são chamados para definir sua condição para o valor especificado no `bpCondition` parâmetro.

## <a name="see-also"></a>Confira também
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
