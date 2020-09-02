---
title: Avaliação de expressão (Visual Studio Debugging SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0f2a84f01168dd01921d933a80fe052c1a6c6447
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562153"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Avaliação de expressão (SDK de depuração do Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durante o modo de interrupção, o IDE deve ser capaz de avaliar expressões simples que envolvam várias variáveis do seu programa. Para fazer isso, o mecanismo de depuração (DE) deve ser capaz de analisar e avaliar uma expressão que é inserida em uma das janelas do IDE.  
  
 As expressões são criadas usando o método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e são representadas pela interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) resultante.  
  
 A interface **IDebugExpression2** é implementada pelo de e chama seu método **EvalAsync** para retornar uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) para o IDE, a fim de exibir os resultados da avaliação da expressão no IDE. [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retorna uma estrutura que pode ser usada para colocar o valor de uma expressão em um janela inspeção ou na janela locais.  
  
 O pacote de depuração ou o SDM (Gerenciador de depuração de sessão) chama [IDebugExpression2:: EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obter uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa o resultado da avaliação. `IDebugProperty2` tem métodos que retornam o nome, o tipo e o valor da expressão. Essas informações são exibidas em várias janelas do depurador.  
  
## <a name="using-expression-evaluation"></a>Usando a avaliação de expressão  
 Para usar a avaliação de expressão, você deve implementar o método [IDebugExpressionContext2::P arsetext](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e todos os métodos da interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) , conforme mostrado na tabela a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia uma expressão de forma assíncrona.|  
|[Anular](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação de expressão assíncrona.|  
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia uma expressão de forma síncrona.|  
  
 A avaliação síncrona e assíncrona requer a implementação do método [IDebugProperty2:: GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) . A avaliação de expressões assíncronas requer a implementação de [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Controle de execução e avaliação de estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
