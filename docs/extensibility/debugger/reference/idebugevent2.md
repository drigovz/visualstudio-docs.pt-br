---
title: IDebugEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6ff87d79d45c90a3307d5f28a2aa6109033f4a59
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933330"
---
# <a name="idebugevent2"></a>IDebugEvent2
Essa interface é usada para comunicar informações de depuração críticas, como parar em um ponto de interrupção e informações não críticas, como uma mensagem de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) e o fornecedor DE porta personalizada implementam essa interface no mesmo objeto que todas as outras interfaces de evento.

## <a name="notes-for-callers"></a>Observações para chamadores
 Usando o argumento IID (ID de interface) fornecido ao [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) ou [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md), o SDM (Session Debug Manager) chama [QueryInterface](/cpp/atl/queryinterface) na `IDebugEvent2` interface para obter a interface de evento apropriada.

## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable
 A tabela a seguir mostra os métodos de `IDebugEvent2` .

|Método|Descrição|
|------------|-----------------|
|[Falha GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtém os atributos para este evento de depuração.|

## <a name="remarks"></a>Comentários
 As interfaces de evento mais específicas, como [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), não derivam da interface IDebugEvent2, mas, em vez disso, são implementadas como uma interface separada no mesmo objeto que `IDebugEvent2` .

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg. h

 Namespace: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
