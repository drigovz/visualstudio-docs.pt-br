---
title: 'IDebugBoundBreakpoint2:: SetPassCount | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80735439"
---
# <a name="idebugboundbreakpoint2setpasscount"></a>IDebugBoundBreakpoint2::SetPassCount
Define ou altera a contagem de aprovações associada a este ponto de interrupção associado.

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
no A estrutura de [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) que especifica a contagem de aprovações.

## <a name="return-value"></a>Valor Retornado
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. Retorna `E_BP_DELETED` se o estado do objeto de ponto de interrupção associado é definido como `BPS_DELETED` (parte da enumeração de [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) ).

## <a name="remarks"></a>Comentários
 A contagem de aprovações determina quando o ponto de interrupção é acionado. A contagem de passagem ou de acesso atual pode ser obtida chamando o método [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md) .

 Qualquer contagem de aprovação que foi associada anteriormente a esse ponto de interrupção é perdida.

## <a name="see-also"></a>Confira também
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [GetHitCount](../../../extensibility/debugger/reference/idebugboundbreakpoint2-gethitcount.md)
- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
