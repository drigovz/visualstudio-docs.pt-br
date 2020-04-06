---
title: Avaliação de expressão (Visual Studio Debugging SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: 5044ced5-c18c-4534-b0bf-cc3e50cd57ac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e41179fd530818f5ac59aa54420ede1b4eafa1ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738718"
---
# <a name="expression-evaluation-visual-studio-debugging-sdk"></a>Avaliação de expressão (Visual Studio Debugging SDK)
Durante o modo de pausa, o IDE deve avaliar expressões simples envolvendo várias variáveis do programa. Para realizar sua avaliação, o motor de depuração (DE) deve analisar e avaliar uma expressão que está inserida em uma das janelas do IDE.

 As expressões são criadas com o método [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e representadas pela interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) resultante.

 A interface **IDebugExpression2** é implementada pelo DE e chama seu método **EvalAsync** para retornar uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) ao IDE, a fim de exibir os resultados da avaliação de expressão no IDE. [IDebugProperty2::GetPropertyInfo](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) retorna uma estrutura que é usada para colocar o valor de uma expressão em uma janela **do relógio** ou na janela **Locals.**

 O SDM (Debug Manager, gerenciador de depuração ou de depuração de depuração) chama [IDebugExpression2::AssessAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) ou [AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) para obter uma interface [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) que representa o resultado da avaliação. `IDebugProperty2`tem métodos que retornam o nome, o tipo e o valor da expressão. Essas informações aparecem em várias janelas de depurador.

## <a name="using-expression-evaluation"></a>Usando avaliação de expressão
 Para usar a avaliação de expressão, você deve implementar o método [IDebugExpressionContext2::ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e todos os métodos da interface [IDebugExpression2,](../../extensibility/debugger/reference/idebugexpression2.md) conforme mostrado na tabela a seguir.

|Método|Descrição|
|------------|-----------------|
|[EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md)|Avalia uma expressão assíncrona.|
|[Abortar](../../extensibility/debugger/reference/idebugexpression2-abort.md)|Termina a avaliação de expressão assíncrona.|
|[EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md)|Avalia uma expressão sincronicamente.|

 A avaliação síncrona e assíncrona requer a implementação do método [IDebugProperty2::GetPropertyInfo.](../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) A avaliação de expressão assíncrona requer a implementação do [IDebugExpressionEvaluationCompleteEvent2](../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md).

## <a name="see-also"></a>Confira também
- [Controle de execução e avaliação do estado](../../extensibility/debugger/execution-control-and-state-evaluation.md)
