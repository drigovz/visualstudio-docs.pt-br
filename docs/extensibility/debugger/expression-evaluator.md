---
title: Avaliador de expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7eda2399b3bd711664e141800c503f31b12e244
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54916544"
---
# <a name="expression-evaluator"></a>Avaliador de expressão
Avaliadores de expressão (EE) examinam a sintaxe de uma linguagem para analisar e avaliar as variáveis e expressões em tempo de execução, permitindo que eles sejam exibidos pelo usuário quando o IDE está no modo de interrupção.  
  
## <a name="use-expression-evaluators"></a>Use os avaliadores de expressão  
 As expressões são criadas usando o [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) método, da seguinte maneira:  
  
1. O mecanismo de depuração (DES) implementa o [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) interface.  
  
2. Obtém o pacote de depuração uma `IDebugExpressionContext2` do objeto de um [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) interface e, em seguida, chama o `IDebugStackFrame2::ParseText` método nele para obter um [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) objeto.  
  
3. As chamadas de pacote de depuração a [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) método ou o [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) método para obter o valor da expressão. `IDebugExpression2::EvaluateAsync` é chamado da janela de comando/imediato. Todos os outros componentes de interface do usuário chamar `IDebugExpression2::EvaluateSync`.  
  
4. O resultado da avaliação da expressão é um [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto, que contém o nome, tipo e valor do resultado da avaliação da expressão.  
  
   Durante a avaliação da expressão, o EE requer informações do componente de provedor de símbolo. O provedor de símbolo fornece as informações simbólicas usadas para identificar e entender a expressão analisada.  
  
   Quando a avaliação da expressão assíncrona for concluída, um evento assíncrono é enviado por DE por meio do Gerenciador de depuração de sessão (SDM) para notificar o IDE que a avaliação da expressão foi concluída. E, o resultado da avaliação, em seguida, é retornado da chamada para o `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Observações sobre a implementação  
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esperam de mecanismos de depuração conversar com o avaliador de expressão usando as interfaces do Common Language Runtime (CLR). Como resultado, um avaliador de expressão que funciona com o [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] mecanismos de depuração devem dar suporte o CLR (uma lista completa de CLR de todas as interfaces de depuração pode ser encontrada em debugref.doc, que é parte do [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]).  
  
## <a name="see-also"></a>Consulte também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)