---
title: IDebugProgramCreateEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramCreateEvent2
helpviewer_keywords:
- IDebugProgramCreateEvent2 interface
ms.assetid: b19a7934-6179-4a68-9075-bd7dcd640b05
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 24a1a1942031dac71ddad7b528f0e5df161c629e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148622"
---
# <a name="idebugprogramcreateevent2"></a>IDebugProgramCreateEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é enviada pelo mecanismo de depuração (DE) para o SDM (Gerenciador de depuração de sessão) quando um programa é anexado ao.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProgramCreateEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O ou o fornecedor de porta personalizada implementa essa interface para relatar que um programa foi criado, normalmente no momento em que o programa está anexado. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface. O SDM usa o `QueryInterface` método para acessar a `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O fornecedor DE porta Personalizada cria e envia esse objeto de evento para relatar a criação de um programa. O DE envia esse evento usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é fornecida pelo SDM quando anexada ao programa que está sendo depurado. O fornecedor da porta personalizada envia esse evento usando a interface [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) .  
  
## <a name="remarks"></a>Comentários  
 O fornecedor DE porta DE ou personalizada publica uma nova interface [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) chamando [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
