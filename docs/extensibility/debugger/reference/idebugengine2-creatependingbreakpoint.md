---
title: IDebugEngine2::CreatePendingBreakpoint | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f88cae3610487b92fed0d8390d44c55d3f536c4b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731124"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
Cria um ponto de ruptura pendente no motor de depuração (DE).

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT CreatePendingBreakpoint(
    IDebugBreakpointRequest2*  pBPRequest,
    IDebugPendingBreakpoint2** ppPendingBP
);
```

```csharp
int CreatePendingBreakpoint(
    IDebugBreakpointRequest2     pBPRequest,
    out IDebugPendingBreakpoint2 ppPendingBP
);
```

## <a name="parameters"></a>parâmetros
`pBPRequest`\
[em] Um objeto [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) que descreve o ponto de ruptura pendente a ser criado.

`ppPendingBP`\
[fora] Retorna um objeto [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) que representa o ponto de ruptura pendente.

## <a name="return-value"></a>Valor retornado
Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. Normalmente `E_FAIL` retorna `pBPRequest` se o parâmetro não corresponder a qualquer idioma `pBPRequest` suportado pelo DE de se o parâmetro estiver inválido ou incompleto.

## <a name="remarks"></a>Comentários
Um ponto de ruptura pendente é essencialmente uma coleta de todas as informações necessárias para vincular um ponto de ruptura ao código. O ponto de ruptura pendente retornado deste método não está vinculado ao código até que o método [Bind](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) seja chamado.

Para cada ponto de ruptura pendente que o usuário define, o SDM (Session Debug Manager, gerenciador de depuração de sessão) chama esse método em cada DE anexado. Cabe ao DE verificar se o ponto de ruptura é válido para programas em execução nesse DE.

Quando o usuário define um ponto de ruptura em uma linha de código, o DE é livre para vincular o ponto de ruptura à linha mais próxima no documento que corresponde a esse código. Isso torna possível que o usuário defina um ponto de ruptura na primeira linha de uma declaração de várias linhas, mas vincule-o na última linha (onde todo o código é atribuído nas informações de depuração).

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como `CProgram` implementar este método para um objeto simples. A implementação do `IDebugEngine2::CreatePendingBreakpoint` DE poderia, então, encaminhar todas as chamadas para esta implementação do método em cada programa.

```
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)
{
    // Create and initialize the CPendingBreakpoint object.
    CComObject<CPendingBreakpoint> *pPending;
    CComObject<CPendingBreakpoint>::CreateInstance(&pPending);
    pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);
    return pPending->QueryInterface(ppPendingBP);
}
```

## <a name="see-also"></a>Confira também
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Associar](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)
- [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
