---
title: IDebugCanStopEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2
helpviewer_keywords:
- IDebugBreakpointRequest2 interface
ms.assetid: 784bd5b1-4a3f-4455-b313-c4c9a82555a5
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bc4ac1f3a8d9b470fbb3734f822601a7dce08a44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696679"
---
# <a name="idebugcanstopevent2"></a>IDebugCanStopEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é usada para solicitar que o SDM (Gerenciador de depuração de sessão) seja interrompido no local do código atual.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugCanStopEvent2 : IUknown  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O mecanismo de depuração (DE) implementa essa interface para dar suporte à depuração por meio do código-fonte. A interface [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) deve ser implementada no mesmo objeto que essa interface (o SDM usa [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar a `IDebugEvent2` interface).  
  
 A implementação dessa interface deve comunicar a chamada do SDM de [canpare](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) para o mecanismo de depuração. Por exemplo, isso pode ser feito com uma mensagem postada no thread de manipulação de mensagens do mecanismo de depuração ou o objeto que implementa essa interface pode conter uma referência ao mecanismo de depuração e retornar ao mecanismo de depuração com o sinalizador passado para `IDebugCanStopEvent2::CanStop` .  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE pode enviar esse método cada vez que o DE é solicitado a continuar a execução e o DE está passando pelo código. Esse evento é enviado usando a função de retorno de chamada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) fornecida pelo SDM quando ele é anexado ao programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 A tabela a seguir mostra os métodos de `IDebugCanStopEvent2` .  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)|Obtém o motivo deste evento.|  
|[CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)|Especifica se o programa que está sendo depurado deve parar no local desse evento (e enviar um evento que descreva o motivo da interrupção) ou apenas continuar a execução.|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)|Obtém o contexto do documento que descreve o local desse evento.|  
|[GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)|Obtém o contexto de código que descreve o local desse evento.|  
  
## <a name="remarks"></a>Comentários  
 O DE enviará essa interface se o usuário seguir uma função e o DE não encontrar informações de depuração ali ou se houver informações de depuração, mas o DE não saberá se o código-fonte pode ser exibido para esse local.  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
