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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6341f8003b962a7f45420b076b23623ebdaf861
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729917"
---
# <a name="idebugevent2"></a>IDebugEvent2
Essa interface é usada para comunicar tanto informações críticas de depuração, como parar em um ponto de interrupção, quanto informações não críticas, como uma mensagem de depuração.

## <a name="syntax"></a>Sintaxe

```
IDebugEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 O mecanismo de depuração (DE) e o fornecedor de porta personalizado implementam essa interface no mesmo objeto que todas as outras interfaces de eventos.

## <a name="notes-for-callers"></a>Observações para chamadores
 Usando o argumento ID (Interface ID) dado a [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) or [Event](../../../extensibility/debugger/reference/idebugportevents2-event.md), o Gerenciador `IDebugEvent2` de depuração de sessão (SDM) chama [queryInterface](/cpp/atl/queryinterface) na interface para obter a interface de evento apropriada.

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugEvent2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Getattributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Obtém os atributos para este evento de depuração.|

## <a name="remarks"></a>Comentários
 As interfaces de evento mais específicas, como [IDebugBreakpointEvent2,](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)não derivam da interface IDebugEvent2, `IDebugEvent2`mas são implementadas como uma interface separada no mesmo objeto que .

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
