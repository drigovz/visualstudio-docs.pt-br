---
title: 'IDebugBoundBreakpoint2:: setcondition | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetCondition
helpviewer_keywords:
- SetCondition method
- IDebugBoundBreakpoint2::SetCondition method
ms.assetid: 5d366876-efed-43d0-8ea1-dfdb009cbfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f23fbe1b353378ca521fa802bdeae25fd12476df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735468"
---
# <a name="idebugboundbreakpoint2setcondition"></a>IDebugBoundBreakpoint2::SetCondition
Define ou altera a condição associada a este ponto de interrupção associado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetCondition( 
   BP_CONDITION bpCondition
);
```

```csharp
int SetCondition( 
   enum_BP_CONDITION bpCondition
);
```

## <a name="parameters"></a>Parâmetros
`bpCondition`\
no Um valor da enumeração [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) que descreve a condição.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de ponto de interrupção associado é definido como `BPS_DELETED` (parte da enumeração de [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Comentários
 Qualquer condição que foi associada anteriormente a esse ponto de interrupção é perdida.

## <a name="see-also"></a>Confira também
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
