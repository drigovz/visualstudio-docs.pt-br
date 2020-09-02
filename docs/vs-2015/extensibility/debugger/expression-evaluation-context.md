---
title: Contexto de avaliação da expressão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluation, context
ms.assetid: a2fd3758-09bd-45ae-8ecc-2d276c0036ba
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 377609cb9f971b667872c198a53b45a6288f2c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152786"
---
# <a name="expression-evaluation-context"></a>Contexto de avaliação de expressão
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Em [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuração, um **contexto de avaliação de expressão**:  
  
- Representa um contexto para avaliação de expressão. Em geral, um contexto de avaliação corresponde ao escopo léxico no qual avaliar variáveis, parâmetros, funções e métodos. Por exemplo, um contexto de avaliação de expressão associado a um quadro de pilha fornecerá o contexto para avaliar variáveis locais, parâmetros de método e membros de classe (se aplicável).  
  
- Existe quando um programa é interrompido em um ponto de interrupção. A própria expressão é uma estrutura de dados que representa uma expressão analisada que está pronta para associação e avaliação dentro do contexto especificado.  
  
     Mais detalhadamente, as expressões são criadas usando o método [ParseText](../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) . Quando uma expressão é avaliada, ela gera uma cadeia de caracteres imprimível que contém o nome e o tipo de variável ou argumento e seu valor. Essa cadeia de caracteres é exibida no janela Inspeção ou na janela locais do IDE.  
  
     Dado um `BSTR` e uma interface [IDebugExpressionContext2](../../extensibility/debugger/reference/idebugexpressioncontext2.md) , um mecanismo DE depuração (de) pode criar uma interface [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) analisando uma expressão. Dada uma `IDebugExpression2` interface, o de pode obter um valor por meio de avaliação de expressão assíncrona ou síncrono. Esse valor, junto com o nome e o tipo da variável ou argumento, é enviado para o IDE para exibição.  
  
## <a name="see-also"></a>Consulte Também  
 [Interfaces de avaliação de expressão](../../extensibility/debugger/reference/expression-evaluation-interfaces.md)   
 [Contextos do depurador](../../extensibility/debugger/debugger-contexts.md)
