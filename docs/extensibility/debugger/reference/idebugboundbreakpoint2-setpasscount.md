---
title: IDebugBoundBreakpoint2::SetPassCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetPassCount
helpviewer_keywords:
- SetPassCount method
- IDebugBoundBreakpoint2::SetPassCount method
ms.assetid: b32c12f9-b34d-43bd-a1b9-61af6cf8e51b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 97e783947055bda86a35bb8b68a44c13da3613c0
ms.sourcegitcommit: 77b4ca625674658d5c5766e684fa0e2a07cad4da
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65614690"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Define ou altera a contagem de passagem associada a este ponto de interrupção associado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

```csharp
int SetPassCount( 
   BP_PASSCOUNT bpPassCount
);
```

## <a name="parameters"></a>Parâmetros
`bpPassCount`\
[in] O [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) estrutura que especifica a contagem de passagem.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto associado de ponto de interrupção é definido como `BPS_DELETED` (parte do [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) enumeração).

## <a name="remarks"></a>Comentários
 A contagem de passagem determina quando o ponto de interrupção é disparado. A contagem de ocorrências ou passagem atual pode ser obtida chamando o [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) método.

 Qualquer contagem de passagem que foi previamente associada este ponto de interrupção é perdida.

## <a name="see-also"></a>Consulte também
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)