---
title: BP_CONDITION | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- BP_CONDITION
helpviewer_keywords:
- BP_CONDITION structure
ms.assetid: 407f87a3-2878-429b-8c65-b68feb36622a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 88ed6b6468c5765c8f987c1f15f3e4e8ade9c8c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738095"
---
# <a name="bp_condition"></a>BP_CONDITION
Descreve as condições sob as quais um ponto de ruptura dispara.

## <a name="syntax"></a>Sintaxe

```cpp
typedef struct _BP_CONDITION {
    IDebugThread2* pThread;
    BP_COND_STYLE  styleCondition;
    BSTR           bstrContext;
    BSTR           bstrCondition;
    UINT           nRadix;
} BP_CONDITION;
```

```csharp
public struct BP_CONDITION {
    public IDebugThread2 pThread;
    public uint          styleCondition;
    public string        bstrContext;
    public string        bstrCondition;
    public uint          nRadix;
};
```

## <a name="members"></a>Membros
`pThread`\
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o segmento ativo para o aplicativo que contém o ponto de ruptura.

`styleCondition`\
Um valor da enumeração [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) descrevendo o estilo desta condição de ponto de ruptura.

`bstrContext`\
A localização do ponto de ruptura.

`bstrCondition`\
A condição de disparo do ponto de ruptura.

`nRadix`\
Radix para ser usado na avaliação de qualquer informação numérica.

## <a name="remarks"></a>Comentários
Esta estrutura é um membro das estruturas [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2.](../../../extensibility/debugger/reference/bp-request-info2.md)

Essa estrutura também é passada como parâmetro para os métodos [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) e [SetCondition.](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
