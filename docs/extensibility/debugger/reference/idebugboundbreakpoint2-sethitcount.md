---
title: IDebugBoundBreakpoint2::SetHitCount | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82f12b12c9afbc24f9416ec2639a4b9768d8fd0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735408"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Define a contagem de acertos para o ponto de ruptura vinculado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>parâmetros
`dwHitCount`\
[em] A contagem de acertos para definir.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de `BPS_DELETED` ponto de ruptura vinculado estiver definido como (parte da [enumeração BP_STATE).](../../../extensibility/debugger/reference/bp-state.md)

## <a name="remarks"></a>Comentários
 A contagem de acertos é o número de vezes que este ponto de partida foi disparado durante a atual execução da sessão.

 Este método é normalmente chamado pelo mecanismo de depuração para atualizar a contagem de acertos atuais neste ponto de breakpoint.

## <a name="see-also"></a>Confira também
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
