---
title: Interface IDebugApplication | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication interface
ms.assetid: 5dfa941b-4cd9-46fa-a230-3f41df9ea205
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8229f234f8a8ce607f36c48e070cb3d40a211d45
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152464"
---
# <a name="idebugapplication-interface"></a>Interface IDebugApplication
Expõe métodos de depuração não remota para uso por hosts e mecanismos de linguagem.  
  
 Além dos métodos herdados de `IRemoteDebugApplication`, o `IDebugApplication` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[IDebugApplication::SetName](../../winscript/reference/idebugapplication-setname.md)|Define o nome do aplicativo.|  
|[IDebugApplication::StepOutComplete](../../winscript/reference/idebugapplication-stepoutcomplete.md)|Notifica o Gerenciador de depuração do processo que um mecanismo de linguagem no modo passo a passo está prestes a retornar a seu chamador.|  
|[IDebugApplication::DebugOutput](../../winscript/reference/idebugapplication-debugoutput.md)|Faz com que a cadeia de caracteres fornecida a ser exibida pelo depurador IDE.|  
|[IDebugApplication::StartDebugSession](../../winscript/reference/idebugapplication-startdebugsession.md)|Inicia o IDE do depurador padrão e anexa a uma sessão de depuração para este aplicativo, se um já não está anexado.|  
|[IDebugApplication::HandleBreakPoint](../../winscript/reference/idebugapplication-handlebreakpoint.md)|Faz com que o thread atual bloquear e envia uma notificação do ponto de interrupção para o IDE do depurador.|  
|[IDebugApplication::Close](../../winscript/reference/idebugapplication-close.md)|Faz com que esse aplicativo para liberar todas as referências e entrar em um estado inativo.|  
|[IDebugApplication::GetBreakFlags](../../winscript/reference/idebugapplication-getbreakflags.md)|Retorna os sinalizadores de interrupção atual para o aplicativo.|  
|[IDebugApplication::GetCurrentThread](../../winscript/reference/idebugapplication-getcurrentthread.md)|Retorna o thread associado ao thread em execução no momento.|  
|[IDebugApplication::CreateAsyncDebugOperation](../../winscript/reference/idebugapplication-createasyncdebugoperation.md)|Fornece acesso assíncrono a uma operação de depuração síncrona determinado.|  
|[IDebugApplication::AddStackFrameSniffer](../../winscript/reference/idebugapplication-addstackframesniffer.md)|Adiciona um provedor de enumerador de quadro de pilha para esse aplicativo.|  
|[IDebugApplication::RemoveStackFrameSniffer](../../winscript/reference/idebugapplication-removestackframesniffer.md)|Remove um provedor de enumerador de quadro de pilha desse aplicativo.|  
|[IDebugApplication::QueryCurrentThreadIsDebuggerThread](../../winscript/reference/idebugapplication-querycurrentthreadisdebuggerthread.md)|Determina se o thread de execução atual é o thread do depurador.|  
|[IDebugApplication::SynchronousCallInDebuggerThread](../../winscript/reference/idebugapplication-synchronouscallindebuggerthread.md)|Fornece um mecanismo para que o chamador executar o código no thread do depurador.|  
|[IDebugApplication::CreateApplicationNode](../../winscript/reference/idebugapplication-createapplicationnode.md)|Cria um novo nó de aplicativo que está associado um provedor de documento específico.|  
|[IDebugApplication::FireDebuggerEvent](../../winscript/reference/idebugapplication-firedebuggerevent.md)|Dispara um evento genérico para o depurador `IApplicationDebugger` interface.|  
|[IDebugApplication::HandleRuntimeError](../../winscript/reference/idebugapplication-handleruntimeerror.md)|Faz com que o thread atual bloquear e envia uma notificação de erro para o IDE do depurador.|  
|[IDebugApplication::FCanJitDebug](../../winscript/reference/idebugapplication-fcanjitdebug.md)|Determina se um depurador do just-in-time (JIT) está registrado.|  
|[IDebugApplication::FIsAutoJitDebugEnabled](../../winscript/reference/idebugapplication-fisautojitdebugenabled.md)|Determina se um depurador JIT está registrado para hosts burros de depuração automática.|  
|[IDebugApplication::AddGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-addglobalexpressioncontextprovider.md)|Adiciona um provedor de contexto de expressão global para este aplicativo.|  
|[IDebugApplication::RemoveGlobalExpressionContextProvider](../../winscript/reference/idebugapplication-removeglobalexpressioncontextprovider.md)|Remove um provedor de contexto de expressão global desse aplicativo.|