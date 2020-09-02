---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 68f1693bbbda9bbf7622c2378799db4a342be7a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187972"
---
# <a name="idebugprocess2"></a>IDebugProcess2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface representa um processo em execução em uma porta. Se a porta for a porta local, `IDebugProcess2` geralmente representa um processo físico no computador local.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 Essa interface é implementada por um fornecedor de porta personalizado para gerenciar programas como um grupo. Essa interface deve ser implementada pelo fornecedor da porta.  
  
 Um mecanismo de depuração também implementa essa interface se oferecer suporte à inicialização de um programa por meio do [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Essa interface é chamada principalmente pelo SDM (Gerenciador de depuração de sessão) para interagir com um grupo de programas identificados nesse processo.  
  
 Chame [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obter essa interface. Essa interface também é retornada chamando `IDebugEngineLaunch2::LaunchSuspended` .  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugProcess2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Obtém uma descrição do processo.|  
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera os programas contidos nesse processo.|  
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtém o título, o nome amigável ou o nome do arquivo do processo.|  
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtém a instância de um servidor de computador em que esse processo está sendo executado.|  
|[Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Encerra o processo.|  
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Anexa ao processo.|  
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se o SDM pode desanexar o processo.|  
|[Desanexar](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Desanexa o depurador do processo.|  
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtém o identificador do processo do sistema.|  
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtém um identificador global exclusivo para esse processo.|  
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> PRETERIDO|Obtém o nome da sessão que está depurando o processo.<br /><br /> Preterido. SEMPRE deve retornar `E_NOTIMPL` .]|  
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera os threads em execução no processo.|  
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita que o próximo programa que executa o código neste processo pare.|  
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Obtém a porta em que esse processo está sendo executado.|  
  
## <a name="remarks"></a>Comentários  
 Um `IDebugProcess2` contém uma ou mais interfaces [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) .  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)   
 [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)   
 [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)   
 [Última](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)   
 [Circunstância](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [Circunstância](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
