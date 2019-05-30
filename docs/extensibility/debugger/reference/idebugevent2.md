---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f87184481c5d01e74d284b175078b67f6f2612d1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310594"
---
# <a name="idebugevent2"></a>IDebugEvent2
Essa interface é usada para comunicar informações de depuração essenciais, como interromper um ponto de interrupção e informações não-críticas, como uma mensagem de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Observações para implementadores
 O mecanismo de depuração (DES) e o fornecedor de porta personalizada implementam essa interface no mesmo objeto, como todas as outras interfaces de evento.

## <a name="notes-for-callers"></a>Observações para chamadores
 Usando a interface do argumento IID (ID) fornecido ao [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), o Gerenciador de sessão de depuração (SDM) chama [QueryInterface](/cpp/atl/queryinterface) no `IDebugEvent2` interface para obter a interface de eventos apropriado.

## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable
 A tabela a seguir mostra os métodos de `IDebugEvent2`.

|Método|Descrição|
|------------|-----------------|
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtém os atributos para este evento de depuração.|

## <a name="remarks"></a>Comentários
 Interfaces de evento mais específico, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), não derivam da interface IDebugEvent2, mas em vez disso, são implementados como uma interface separada no mesmo objeto como `IDebugEvent2`.

## <a name="requirements"></a>Requisitos
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Consulte também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)