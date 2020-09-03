---
title: IDebugEventCallback2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEventCallback2
helpviewer_keywords:
- IDebugEventCallback2
ms.assetid: 2c935ee0-2e22-4be0-a852-73736f33c8c9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6114a31701e5abc4714f315b4e4f1ecf022c401c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163821"
---
# <a name="idebugeventcallback2"></a>IDebugEventCallback2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é usada pelo mecanismo de depuração (DE) para enviar eventos de depuração para o SDM (Gerenciador de depuração de sessão).  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugEventCallback2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implementa essa interface para receber eventos de um mecanismo de depuração.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Um mecanismo de depuração normalmente recebe essa interface quando o SDM chama [Attach](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md). Um mecanismo de depuração envia eventos para o SDM chamando [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugEventCallback2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)|Envia a notificação de eventos de depuração para o SDM.|  
  
## <a name="remarks"></a>Comentários  
 Embora [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) e [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) especifiquem que eles usam uma `IDebugEventCallback2` interface, esse não é o caso e o ponteiro de interface sempre será um valor nulo. Em vez disso, o mecanismo de depuração deve usar a `IDebugEventCallback2` interface recebida na chamada para [anexar](../../../extensibility/debugger/reference/idebugprogram2-attach.md), [anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)ou [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
 Se um pacote implementa [IDebugEventCallback](../../../extensibility/debugger/reference/idebugeventcallback2.md) em código gerenciado, é altamente recomendável que <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> seja chamado nas várias interfaces que são passadas para o [evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [Anexa](../../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
