---
title: Contexto de Avaliação de Expressão | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e939a4fa5f4673e2f701206c96599c54bc0c3b51
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738740"
---
# <a name="expression-evaluation-context"></a>Contexto de avaliação de expressão
Na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuração, um **contexto de avaliação de expressão:**

- Representa um contexto para avaliação de expressão. Geralmente, um contexto de avaliação corresponde ao escopo léxico no qual se avalia variáveis, parâmetros, funções e métodos. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornecerá o contexto para avaliar variáveis locais, parâmetros de método e membros de classe (se aplicável).

- Existe quando um programa parou em um ponto de ruptura. A expressão em si é uma estrutura de dados representando uma expressão parsed que está pronta para vincular e avaliar dentro do contexto dado.

     Em mais detalhes, expressões são criadas usando o método [ParseText.](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) Quando uma expressão é avaliada, ela gera uma seqüência imprimível contendo o nome e o tipo de variável ou argumento e seu valor. Esta seqüência é exibida na janela do relógio ou na janela Locals do IDE.

     Dada `BSTR` a e uma interface [IDebugExpressionContext2,](../../extensibility/debugger/reference/idebugexpressioncontext2.md) um mecanismo de depuração (DE) pode criar uma interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analisando uma expressão. Dada `IDebugExpression2` uma interface, o DE pode obter um valor através de avaliação de expressão síncrona ou assíncrona. Este valor, juntamente com o nome e o tipo da variável ou argumento, é enviado ao IDE para exibição.

## <a name="see-also"></a>Confira também
- [Interfaces de avaliação de expressão](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [Contextos de depuração](../../extensibility/debugger/debugger-contexts.md)
