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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bcc7bd57ce0c392a2874f107c6e4d8d5753399d3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735439"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Define ou altera a contagem de passes associada a este ponto de ruptura vinculado.

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

## <a name="parameters"></a>parâmetros
`bpPassCount`\
[em] A estrutura [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que especifica a contagem de passes.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de `BPS_DELETED` ponto de ruptura vinculado estiver definido como (parte da [enumeração BP_STATE).](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Comentários
 A contagem de passes determina quando o ponto de partida é disparado. A contagem atual de passes ou acessadas pode ser obtida chamando o método [GetHitCount.](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)

 Qualquer contagem de passes que foi anteriormente associada a este ponto de ruptura está perdida.

## <a name="see-also"></a>Confira também
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
