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
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 8bbdcec09ef004817b05e7992ae72bc856764da9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945845"
---
# <a name="bp_condition"></a>BP_CONDITION
Descreve as condições sob as quais um ponto de interrupção é acionado.

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
O objeto [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) que representa o thread ativo para o aplicativo que contém o ponto de interrupção.

`styleCondition`\
Um valor da enumeração de [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md) que descreve o estilo dessa condição de ponto de interrupção.

`bstrContext`\
O local do ponto de interrupção.

`bstrCondition`\
A condição de acionamento do ponto de interrupção.

`nRadix`\
Base a ser usada na avaliação de qualquer informação numérica.

## <a name="remarks"></a>Comentários
Essa estrutura é um membro das estruturas [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) e [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) .

Essa estrutura também é passada como um parâmetro para os métodos [setcondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md) e [setcondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md) .

## <a name="requirements"></a>Requisitos
Cabeçalho: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Estruturas e uniões](../../../extensibility/debugger/reference/structures-and-unions.md)
- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)
- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugboundbreakpoint2-setcondition.md)
- [SetCondition](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-setcondition.md)
- [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)
- [BP_COND_STYLE](../../../extensibility/debugger/reference/bp-cond-style.md)
