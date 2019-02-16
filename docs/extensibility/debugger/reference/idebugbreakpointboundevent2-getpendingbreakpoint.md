---
title: IDebugBreakpointBoundEvent2::GetPendingBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
helpviewer_keywords:
- IDebugBreakpointBoundEvent2::GetPendingBreakpoint
ms.assetid: 6da7ed86-b412-4964-b6a3-0687a66f63fe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4039a8ca3b6759480ff1df7b2a9f648ae4ad01e9
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56316152"
---
# <a name="idebugbreakpointboundevent2getpendingbreakpoint"></a>IDebugBreakpointBoundEvent2::GetPendingBreakpoint
Obtém o ponto de interrupção pendente que está sendo associado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetPendingBreakpoint(
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```cpp
int GetPendingBreakpoint(
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

#### <a name="parameters"></a>Parâmetros
`ppPendingBP`  
[out] Retorna o [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) objeto que representa o ponto de interrupção pendente que está sendo associado.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um **CBreakpointSetDebugEventBase** objeto que expõe a [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) interface.

```cpp
STDMETHODIMP CBreakpointSetDebugEventBase::GetPendingBreakpoint(
    IDebugPendingBreakpoint2 **ppPendingBP)
{
    HRESULT hRes = E_FAIL;

    if ( ppPendingBP )
    {
        if ( m_pPendingBP )
        {
            *ppPendingBP = m_pPendingBP;

            m_pPendingBP->AddRef();

            hRes = S_OK;
        }
        else
            hRes = E_FAIL;
    }
    else
        hRes = E_INVALIDARG;

    return ( hRes );
}
```

## <a name="see-also"></a>Consulte também
[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)  
[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
