---
title: IDebugCoreServer3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3
helpviewer_keywords:
- IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1781b133b4c3ee95b4207a0dd237e2dd7298a1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685644"
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface fornece acesso a informações sobre o servidor em que o processo está sendo executado.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O Visual Studio implementa essa interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Use [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para obter essa interface de uma interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) . Uma chamada para [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) também pode retornar essa interface. Essa interface é usada com mais frequência por um fornecedor de porta personalizado para iniciar programas em um servidor (local ou remoto).  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 Além dos métodos na interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) , essa interface implementa os seguintes métodos:  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Recupera o nome do servidor.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Recupera uma versão amigável do nome do servidor|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Informa aos mecanismos de depuração específicos para anexar automaticamente aos processos quando esses processos são iniciados.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Recupera um código de erro específico quando o anexo automático falha.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Cria uma instância de um mecanismo de depuração no servidor.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Recupera um sinalizador que indica se o servidor está no mesmo computador que o chamador.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Recupera um valor que indica o protocolo que está sendo usado para se comunicar com o servidor.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Desabilita todas as configurações de anexo automático para todos os mecanismos de depuração sobre os quais este servidor sabe.|  
  
## <a name="remarks"></a>Comentários  
 Um fornecedor de porta personalizado recebe a interface [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) em uma chamada para [evento](../../../extensibility/debugger/reference/idebugportevents2-event.md). A `IDebugCoreServer3` interface pode ser obtida a partir dessa interface.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)
