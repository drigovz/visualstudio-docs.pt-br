---
title: IDebugStackFrame3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame3
helpviewer_keywords:
- IDebugStackFrame3 interface
ms.assetid: 39af2f57-0a01-42b8-b093-b7fbc61e2909
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d63d4dcd6e3b7a3b81504b485ee710779cef3c13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65688530"
---
# <a name="idebugstackframe3"></a>IDebugStackFrame3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface estende [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para manipular exceções interceptadas.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStackFrame3 : IDebugStackFrame2  
```  
  
## <a name="notes-for-implementers"></a>Notas para implementadores  
 O mecanismo de depuração (DE) implementa essa interface no mesmo objeto que implementa a interface [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) para dar suporte a exceções interceptadas.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 Chame [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) em uma `IDebugStackFrame2` interface para obter essa interface.  
  
## <a name="methods-in-vtable-order"></a>Métodos em ordem vtable  
 Além dos métodos herdados de [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md), `IDebugStackFrame3` o expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)|Manipula uma exceção para o quadro de pilhas atual antes de qualquer manipulação de exceção regular.|  
|[GetUnwindCodeContext](../../../extensibility/debugger/reference/idebugstackframe3-getunwindcodecontext.md)|Retorna um contexto de código se um desenrolamento de pilha ocorrer.|  
  
## <a name="remarks"></a>Comentários  
 Uma exceção interceptada significa que um depurador pode processar uma exceção antes que qualquer rotina de manipulação de exceção normal seja chamada pelo tempo de execução. Interceptar uma exceção essencialmente significa fazer o tempo de execução fingir que há um manipulador de exceção presente mesmo quando não há.  
  
 [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) é chamado durante todos os eventos de retorno de chamada de exceção normal (a única exceção é se você estiver depurando código de modo misto (código gerenciado e não gerenciado). nesse caso, a exceção não pode ser interceptada durante o retorno de chamada de última chance). Se o DE não implementar `IDebugStackFrame3` ou o de retornar um erro de IDebugStackFrame3:: `InterceptCurrentException` (como `E_NOTIMPL` ), o depurador tratará a exceção normalmente.  
  
 Ao interceptar uma exceção, o depurador pode permitir que o usuário faça alterações no estado do programa que está sendo depurado e, em seguida, retome a execução no ponto em que a exceção foi gerada.  
  
> [!NOTE]
> As exceções interceptadas são permitidas somente em código gerenciado, ou seja, em um programa em execução no CLR (Common Language Runtime).  
  
 Um mecanismo de depuração indica que ele dá suporte à interceptação de exceções, definindo "metricExceptions" como um valor de 1 em tempo de execução usando a `SetMetric` função. Para obter mais informações, consulte [auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md).  
  
## <a name="requirements"></a>Requisitos  
 Cabeçalho: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces principais](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [Auxiliares do SDK para depuração](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
