---
title: IDebugProgram2::Attach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5415a79b3c371f89b215f65c54f371eeb0319ead
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53947615"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
Anexa ao programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pCallback`  
 [in] Uma [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto a ser usado para notificação de eventos de depuração.  
  
## <a name="return-value"></a>Valor de retorno  
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra algumas possíveis códigos de erro.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O programa especificado já está anexado ao depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ocorreu uma violação de segurança durante o procedimento de anexação.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um programa de desktop não pode ser anexado ao depurador.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo de depuração (DES) nunca chama esse método para conectar a um programa. Se a Alemanha é executado no espaço de endereço do programa, o [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) método é chamado. Se as execuções DE no Gerenciador de depuração de sessão (SDM) endereço espaço, o [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) método é chamado.  
  
## <a name="see-also"></a>Consulte também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Anexar](../../../extensibility/debugger/reference/idebugengine2-attach.md)