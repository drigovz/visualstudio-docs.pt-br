---
title: 'IDebugProgram2:: Attach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0e029c2e16d5eee1764b463b21fc0fd8a4032252
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62580398"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Anexa ao programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp#  
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
 no Um objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) a ser usado para a notificação de evento de depuração.  
  
## <a name="return-value"></a>Valor Retornado  
 Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro. A tabela a seguir mostra alguns códigos de erro possíveis.  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O programa especificado já está anexado ao depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Ocorreu uma violação de segurança durante o procedimento de anexação.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um programa de área de trabalho não pode ser anexado ao depurador.|  
  
## <a name="remarks"></a>Comentários  
 Um mecanismo DE depuração (DE) nunca chama esse método para anexar a um programa. Se o DE for executado no espaço de endereço do programa, o método [onattach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) será chamado. Se o DE for executado no espaço de endereço do SDM (Gerenciador de depuração de sessão), o método [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) será chamado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [Desanexar](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
