---
title: IDebugPortEx2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortEx2
helpviewer_keywords:
- IDebugPortEx2 interface
ms.assetid: 144724d0-38ee-4c9b-87ca-8a504371182b
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35a1acf88acda7a96dffc10706b8467253ae816d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926434"
---
# <a name="idebugportex2"></a>IDebugPortEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface permite que a sessão de depuração (SDM) Gerenciador controle programas e processos em execução em uma porta.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugPortEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto que implementa [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md).  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 As chamadas SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sobre o `IDebugPort2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugPortEx2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)|Um arquivo executável é iniciado.|  
|[ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)|Retoma a execução de um processo.|  
|[CanTerminateProcess](../../../extensibility/debugger/reference/idebugportex2-canterminateprocess.md)|Determina se um processo pode ser encerrado.|  
|[TerminateProcess](../../../extensibility/debugger/reference/idebugportex2-terminateprocess.md)|Finaliza um processo.|  
|[GetPortProcessId](../../../extensibility/debugger/reference/idebugportex2-getportprocessid.md)|Obtém a ID de processo da porta em si.|  
|[GetProgram](../../../extensibility/debugger/reference/idebugportex2-getprogram.md)|Obtém um programa associado a um nó de programa.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é normalmente privada entre o SDM e o fornecedor de porta personalizada.  
  
 Se desejado, um mecanismo de depuração (DES) pode procurar essa interface [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface é passada para [LaunchSuspended](../../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) e use [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) para iniciar o programa. No entanto, isso é não é um requisito, e a DE pode fazer tudo o que ele precisa para iniciar o programa de solicitação.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
