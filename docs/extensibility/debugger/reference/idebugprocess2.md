---
title: IDebugProcess2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2
helpviewer_keywords:
- IDebugProcess2 interface
ms.assetid: 99f6cd06-4076-45ee-b2ae-fa2ad627fd18
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c72659491ec6718397a4fbb494175eea0896c7f7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80723802"
---
# <a name="idebugprocess2"></a>IDebugProcess2
Esta interface representa um processo em execução em uma porta. Se a porta é a `IDebugProcess2` porta local, então geralmente representa um processo físico na máquina local.

## <a name="syntax"></a>Sintaxe

```
IDebugProcess2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notas para implementadores
 Essa interface é implementada por um fornecedor de porto personalizado para gerenciar programas em grupo. Esta interface deve ser implementada pelo fornecedor portuário.

 Um mecanismo de depuração também implementa essa interface se ele suportar o lançamento de um programa através [do LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md).

## <a name="notes-for-callers"></a>Observações para chamadores
 Essa interface é chamada principalmente pelo Session Debug Manager (SDM) para interagir com um grupo de programas identificados nesse processo.

 Ligue para [getprocess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md) ou [getprocess](../../../extensibility/debugger/reference/idebugport2-getprocess.md) para obter esta interface. Esta interface também é `IDebugEngineLaunch2::LaunchSuspended`retornada por chamada .

## <a name="methods-in-vtable-order"></a>Métodos em Ordem Vtable
 A tabela a seguir `IDebugProcess2`mostra os métodos de .

|Método|Descrição|
|------------|-----------------|
|[GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md)|Tem uma descrição do processo.|
|[EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)|Enumera os programas contidos nesse processo.|
|[GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)|Obtém o título, nome amigável ou nome do arquivo do processo.|
|[GetServer](../../../extensibility/debugger/reference/idebugprocess2-getserver.md)|Obtém a instância de um servidor de máquina que este processo está sendo executado.|
|[Encerrar](../../../extensibility/debugger/reference/idebugprocess2-terminate.md)|Termina o processo.|
|[Attach](../../../extensibility/debugger/reference/idebugprocess2-attach.md)|Anexa-se ao processo.|
|[CanDetach](../../../extensibility/debugger/reference/idebugprocess2-candetach.md)|Determina se o SDM pode separar o processo.|
|[Detach](../../../extensibility/debugger/reference/idebugprocess2-detach.md)|Destaca o depurador do processo.|
|[GetPhysicalProcessId](../../../extensibility/debugger/reference/idebugprocess2-getphysicalprocessid.md)|Obtém o identificador do processo do sistema.|
|[GetProcessId](../../../extensibility/debugger/reference/idebugprocess2-getprocessid.md)|Obtém um identificador globalmente único para este processo.|
|[GetAttachedSessionName](../../../extensibility/debugger/reference/idebugprocess2-getattachedsessionname.md)<br /><br /> [PRETERIDO]|Obtém o nome da sessão que está depurando o processo.<br /><br /> [PRETERIDO. DEVE SEMPRE `E_NOTIMPL`VOLTAR .]|
|[EnumThreads](../../../extensibility/debugger/reference/idebugprocess2-enumthreads.md)|Enumera os fios em execução no processo.|
|[CauseBreak](../../../extensibility/debugger/reference/idebugprocess2-causebreak.md)|Solicita que o próximo programa que executa o código neste processo pare.|
|[GetPort](../../../extensibility/debugger/reference/idebugprocess2-getport.md)|Fica com a porta em que este processo está sendo executado.|

## <a name="remarks"></a>Comentários
 Um `IDebugProcess2` contém uma ou mais interfaces [IDebugProgram2.](../../../extensibility/debugger/reference/idebugprogram2.md)

## <a name="requirements"></a>Requisitos
 Cabeçalho: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Montagem: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Confira também
- [Principais interfaces](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md)
- [GetProcess](../../../extensibility/debugger/reference/idebugprogram2-getprocess.md)
- [Avançar](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)
- [Evento](../../../extensibility/debugger/reference/idebugportevents2-event.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [Evento](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
