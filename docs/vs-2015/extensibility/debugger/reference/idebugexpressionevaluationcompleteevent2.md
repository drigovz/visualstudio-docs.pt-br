---
title: IDebugExpressionEvaluationCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugExpressionEvaluationCompleteEvent2
helpviewer_keywords:
- IDebugExpressionEvaluationCompleteEvent2
ms.assetid: d538fc19-55bf-4231-9595-eb01e84fd1d8
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a7692a06004a1f9d31a31f91c081c6168d89a8dc
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65694385"
---
# <a name="idebugexpressionevaluationcompleteevent2"></a>IDebugExpressionEvaluationCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Essa interface é enviada pelo mecanismo de depuração (DE) para o Gerenciador de sessão de depuração (SDM) quando a avaliação da expressão assíncrona for concluída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
IDebugExpressionEvaluationCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Observações para implementadores  
 O DE implementa essa interface para reportar conclusão de uma avaliação de expressão iniciada por uma chamada para [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md). O [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interface deve ser implementada no mesmo objeto como essa interface. Usa o SDM [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) para acessar o `IDebugEvent2` interface.  
  
## <a name="notes-for-callers"></a>Observações para chamadores  
 O DE cria e envia esse objeto de evento para relatar a conclusão de uma avaliação de expressão. O evento é enviado usando o [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) função de retorno de chamada que é fornecida pelo SDM quando anexado a programa que está sendo depurado.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
 A tabela a seguir mostra os métodos de `IDebugExpressionEvaluationCompleteEvent2`.  
  
|Método|Descrição|  
|------------|-----------------|  
|[GetExpression](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getexpression.md)|Obtém a expressão original.|  
|[GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md)|Obtém o resultado da avaliação de expressão.|  
  
## <a name="remarks"></a>Comentários  
 O DE deve enviar esse evento, se a avaliação foi bem-sucedida ou não.  
  
 Se a avaliação não foi bem-sucedida, o `DEBUG_PROPINFO_VALUE` e `DEBUG_PROPINFO_ATTRIB` sinalizadores não serão definidos [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) estrutura que é retornada por [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) (o [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) criado pelo DE e retornado no objeto de `IDebugExpressionEvaluationCompleteEvent2` evento se a avaliação falhar).  
  
## <a name="requirements"></a>Requisitos  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte também  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
