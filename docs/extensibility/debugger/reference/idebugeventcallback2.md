---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a74825a955afdde03e63673c4b1b6afda5904953
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729888"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
Esta interface é usada pelo mecanismo de depuração (DE) para enviar eventos de depuração para o Gerenciador de depuração de sessão (SDM).

## <a name="syntax"></a>Sintaxe

```
IDebugEventCallback2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementa esta interface para receber eventos de um mecanismo de depuração.

## <a name="notes-for-callers"></a>Observações para chamadores
 Um mecanismo de depuração normalmente recebe essa interface quando o SDM chama [Attach,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Um mecanismo de depuração envia eventos para o SDM chamando [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugEventCallback2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envia notificação de eventos de depuração para o SDM.|

## <a name="remarks"></a>Comentários
 Embora [o AssessSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [o AssessAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especifiquem que eles tomam uma `IDebugEventCallback2` interface, este não é o caso, e o ponteiro de interface sempre será um valor nulo. Em vez disso, o `IDebugEventCallback2` mecanismo de depuração deve usar a interface recebida na chamada para [Anexar,](../../../extensibility/debugger/reference/idebugprogram2-attach.md) [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou [IniciarSuspenso](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

 Se um pacote implementar [iDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) em código gerenciado, <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> é fortemente aconselhável que seja invocado nas várias interfaces que são passadas para [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).

## <a name="requirements"></a>Requisitos
 Cabeçalho: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
