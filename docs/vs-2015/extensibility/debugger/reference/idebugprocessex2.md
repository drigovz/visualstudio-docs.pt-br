---
title: IDebugProcessEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a89eb4a770371d19e0c7b422fcac2a08d142f731
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49207838"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface permite que a sessão de Gerenciador de depuração (SDM) notificar um processo que está anexando a ou desanexar do processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugProcessEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 Um fornecedor de porta personalizada implementa essa interface no mesmo objeto como o [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) de interface para:  
  
-   Suporte ao acompanhamento de sessões conectadas a um processo  
  
-   Suporte a anexação automática entre vários mecanismos de depuração  
  
 O fornecedor de porta personalizada pode implementar essa interface se optar por.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
  
-   As chamadas SDM [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em um `IDebugProcess2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugProcessEx2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[Anexar](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|Informa o processo que uma sessão agora está depurando o processo.|  
|[Desanexar](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Informa o processo que uma sessão não está depurando o processo.|  
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Adiciona nós de programa para obter uma lista de mecanismos de depuração.|  
  
## <a name="remarks"></a>Comentários  
 Essa interface é privada entre o SDM e o processo.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: Portpriv.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [Principais Interfaces](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

