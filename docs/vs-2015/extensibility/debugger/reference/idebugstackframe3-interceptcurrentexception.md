---
title: 'IDebugStackFrame3:: InterceptCurrentException | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3::InterceptCurrentException
helpviewer_keywords:
- IDebugStackFrame3::InterceptCurrentException
ms.assetid: 116c7324-7645-4c15-b484-7a5cdd065ef5
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42472690431d48a9baafbb0abee27c1a07d24fcd
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2020
ms.locfileid: "91403863"
---
# <a name="idebugstackframe3interceptcurrentexception"></a>IDebugStackFrame3::InterceptCurrentException
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Chamado pelo depurador no quadro de pilha atual quando deseja interceptar a exceção atual.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InterceptCurrentException(  
   INTERCEPT_EXCEPTION_ACTION dwFlags,  
   UINT64*                    pqwCookie  
);  
```  
  
```csharp  
int InterceptCurrentException(  
   uint dwFlags,   
   out  ulong pqwCookie  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwFlags`  
 no Especifica ações diferentes. Atualmente, somente o valor de [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md) tem `IEA_INTERCEPT` suporte e deve ser especificado.  
  
 `pqwCookie`  
 fora Valor exclusivo que identifica uma exceção específica.  
  
## <a name="return-value"></a>Valor retornado  
 Se for bem-sucedido, retornará S_OK; caso contrário, retorna um código de erro.  
  
 Veja a seguir os retornos de erro mais comuns.  
  
|Erro|Descrição|  
|-----------|-----------------|  
|`E_EXCEPTION_CANNOT_BE_INTERCEPTED`|A exceção atual não pode ser interceptada.|  
|`E_EXCEPTION_CANNOT_UNWIND_ABOVE_CALLBACK`|O quadro de execução atual ainda não foi procurado um manipulador.|  
|`E_INTERCEPT_CURRENT_EXCEPTION_NOT_SUPPORTED`|Este método não tem suporte para este quadro.|  
  
## <a name="remarks"></a>Comentários  
 Quando uma exceção é lançada, o depurador obtém o controle do tempo de execução em pontos-chave durante o processo de tratamento de exceção. Durante esses momentos chave, o depurador poderá solicitar o registro de ativação atual se o quadro quiser interceptar a exceção. Dessa forma, uma exceção interceptada é essencialmente um manipulador de exceção em tempo real para um registro de ativação, mesmo que esse quadro de pilha não tenha um manipulador de exceção (por exemplo, um bloco try/catch no código do programa).  
  
 Quando o depurador quiser saber se a exceção deve ser interceptada, ela chamará esse método no objeto de quadro de pilha atual. Esse método é responsável por lidar com todos os detalhes da exceção. Se a interface [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md) não for implementada ou o `InterceptStackException` método retornar qualquer erro, o depurador continuará processando a exceção normalmente.  
  
> [!NOTE]
> As exceções só podem ser interceptadas em código gerenciado, ou seja, quando o programa que está sendo depurado está em execução no tempo de execução do .NET. É claro que os implementadores de linguagem de terceiros podem implementar `InterceptStackException` em seus próprios mecanismos de depuração se escolherem.  
  
 Depois que a interceptação for concluída, um [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) será sinalizado.  
  
## <a name="see-also"></a>Consulte Também  
 [IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)   
 [INTERCEPT_EXCEPTION_ACTION](../../../extensibility/debugger/reference/intercept-exception-action.md)   
 [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)
