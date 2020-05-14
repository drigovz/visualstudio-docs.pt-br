---
title: Avaliador de Expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expressions [Debugging SDK]
- debugging [Debugging SDK], expression evaluation
- expression evaluation
ms.assetid: f9381b2f-99aa-426c-aea0-d9c15f3c859b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a477aaceb57e6ccd2eb5125fcf9d8af9be59472b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738681"
---
# <a name="expression-evaluator"></a>Avaliador de expressão
Os avaliadores de expressão (EE) examinam a sintaxe de uma linguagem para analisar e avaliar variáveis e expressões no tempo de execução, permitindo que sejam visualizadas pelo usuário quando o IDE estiver no modo de pausa.

## <a name="use-expression-evaluators"></a>Use avaliadores de expressão
 Expressões são criadas usando o método [ParseText,](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) da seguinte forma:

1. O mecanismo de depuração (DE) implementa a interface [IDebugExpressionContext2.](../../extensibility/debugger/reference/idebugexpressioncontext2.md)

2. O pacote de `IDebugExpressionContext2` depuração obtém um objeto de uma `IDebugStackFrame2::ParseText` interface [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md) e, em seguida, chama o método nele para obter um objeto [IDebugExpression2.](../../extensibility/debugger/reference/idebugexpression2.md)

3. O pacote de depuração chama o método [AssessSync](../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) ou o método [AssessAsync](../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) para obter o valor da expressão. `IDebugExpression2::EvaluateAsync`é chamado da janela Comando/Imediato. Todos os outros componentes da UI chamam `IDebugExpression2::EvaluateSync`.

4. O resultado da avaliação de expressão é um objeto [IDebugProperty2,](../../extensibility/debugger/reference/idebugproperty2.md) que contém o nome, o tipo e o valor do resultado da avaliação de expressão.

   Durante a avaliação de expressão, o EE requer informações do componente do provedor de símbolos. O provedor de símbolos fornece as informações simbólicas usadas para identificar e entender a expressão analisado.

   Quando a avaliação de expressão assíncrona é concluída, um evento assíncrono é enviado pelo DE através do gerenciador de depuração de sessão (SDM) para notificar o IDE de que a avaliação de expressão está completa. E, o resultado da avaliação é então devolvido `IDebugExpression2::EvaluateSync` da chamada para o método.

## <a name="implementation-notes"></a>Notas de implementação
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] motores de depuração esperam conversar com o avaliador de expressão usando interfaces CLR (Common Language Runtime). Como resultado, um avaliador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] expressão que trabalha com os motores de depuração deve suportar o CLR (uma lista completa de todas [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]as interfaces de depuração CLR pode ser encontrada em debugref.doc, que faz parte do ).

## <a name="see-also"></a>Confira também
- [Componentes do depurador](../../extensibility/debugger/debugger-components.md)
