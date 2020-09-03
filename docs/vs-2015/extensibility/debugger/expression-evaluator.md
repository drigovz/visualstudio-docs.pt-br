---
title: Avaliador de expressão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 423df66e8bd6bc1257a32236aa4ffbb28b80d655
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152747"
---
# <a name="expression-evaluator"></a>Avaliador de expressão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Os avaliadores de expressão (EE) examinam a sintaxe de um idioma para analisar e avaliar variáveis e expressões em tempo de execução, permitindo que eles sejam exibidos pelo usuário quando o IDE estiver no modo de interrupção.  
  
## <a name="using-expression-evaluators"></a>Usando avaliadores de expressão  
 As expressões são criadas usando o método [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) , da seguinte maneira:  
  
1. O mecanismo de depuração (DE) implementa a interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) .  
  
2. O pacote de depuração Obtém um `IDebugExpressionContext2` objeto de uma interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) e, em seguida, chama o `IDebugStackFrame2::ParseText` método nele para obter um objeto [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) .  
  
3. O pacote de depuração chama o método [EvaluateSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou o método [EvaluateAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter o valor da expressão. `IDebugExpression2::EvaluateAsync` é chamado na janela comando/imediato. Todos os outros componentes da interface do usuário chamam `IDebugExpression2::EvaluateSync` .  
  
4. O resultado da avaliação de expressão é um objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) , que contém o nome, o tipo e o valor do resultado da avaliação da expressão.  
  
   Durante a avaliação da expressão, o EE requer informações do componente de provedor de símbolo. O provedor de símbolos fornece as informações simbólicas usadas para identificar e compreender a expressão analisada.  
  
   Quando a avaliação de expressão assíncrona é concluída, um evento assíncrono é enviado pelo por meio do SDM (Gerenciador de depuração de sessão) para notificar o IDE de que a avaliação da expressão foi concluída. Quando a avaliação de expressão síncrona for concluída, o resultado da avaliação será retornado da chamada para o `IDebugExpression2::EvaluateSync` método.  
  
## <a name="implementation-notes"></a>Notas da implementação  
 Os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismos de depuração esperam conversar com o avaliador de expressão usando interfaces CLR (Common Language Runtime). Como resultado, um avaliador de expressão que funciona com os [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] mecanismos de depuração deve dar suporte ao CLR (uma lista completa de todas as interfaces de depuração de CLR pode ser encontrada em debugref.doc, que faz parte do [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] ).  
  
## <a name="see-also"></a>Consulte Também  
 [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
