---
title: Interface IRemoteDebugApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IRemoteDebugApplication interface
ms.assetid: 96bf2a3f-049f-46ba-86ad-57fc184343a2
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a231818def210f7c88ab031059f8561c67b33d1
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159147"
---
# <a name="iremotedebugapplication-interface"></a>Interface IRemoteDebugApplication
Representa um aplicativo em execução. Ele não precisa corresponder a um processo do sistema operacional. Normalmente, um depurador destina-se um aplicativo para depuração. O Gerenciador de depuração do processo normalmente implementa o objeto de aplicativo.  
  
 Além dos métodos herdados de `IUnknown`, o `IRemoteDebugApplication` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IRemoteDebugApplication::ResumeFromBreakPoint](../../winscript/reference/iremotedebugapplication-resumefrombreakpoint.md)|Continua um aplicativo que está atualmente em um ponto de interrupção.|  
|[IRemoteDebugApplication::CauseBreak](../../winscript/reference/iremotedebugapplication-causebreak.md)|Faz com que o aplicativo para invadir o depurador na primeira oportunidade.|  
|[IRemoteDebugApplication::ConnectDebugger](../../winscript/reference/iremotedebugapplication-connectdebugger.md)|Conecta-se um depurador para este aplicativo.|  
|[IRemoteDebugApplication::DisconnectDebugger](../../winscript/reference/iremotedebugapplication-disconnectdebugger.md)|Desconecta o depurador atual do aplicativo.|  
|[IRemoteDebugApplication::GetDebugger](../../winscript/reference/iremotedebugapplication-getdebugger.md)|Retorna o depurador atual conectado ao aplicativo.|  
|[IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md)|Fornece um mecanismo para o depurador do IDE, em execução fora de processo para o aplicativo, para criar objetos no processo do aplicativo.|  
|[IRemoteDebugApplication::QueryAlive](../../winscript/reference/iremotedebugapplication-queryalive.md)|Indica se o aplicativo está respondendo.|  
|[IRemoteDebugApplication::EnumThreads](../../winscript/reference/iremotedebugapplication-enumthreads.md)|Enumera todos os threads conhecidos a serem associados com o aplicativo.|  
|[IRemoteDebugApplication::GetName](../../winscript/reference/iremotedebugapplication-getname.md)|Retorna o nome deste nó de aplicativo.|  
|[IRemoteDebugApplication::GetRootNode](../../winscript/reference/iremotedebugapplication-getrootnode.md)|Retorna o nó de aplicativo no qual todos os nós associados ao aplicativo serão adicionados.|  
|[IRemoteDebugApplication::EnumGlobalExpressionContexts](../../winscript/reference/iremotedebugapplication-enumglobalexpressioncontexts.md)|Enumera os contextos de expressão global para todos os idiomas em execução neste aplicativo.|