---
title: Alterando o valor de um local | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, changing values programmatically
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 516725510c5f5bc7baa8bd96d3f7fb969b6589e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838295"
---
# <a name="changing-the-value-of-a-local"></a>Alterando o valor de um local
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Quando um novo valor é digitado no campo valor da janela **locais** , o pacote de depuração passa a cadeia de caracteres, conforme digitado, para o avaliador de expressão (EE). O EE avalia essa cadeia de caracteres, que pode conter um valor simples ou uma expressão, e armazena o valor resultante no local associado.  
  
 Esta é uma visão geral do processo de alteração do valor de um local:  
  
1. Depois que o usuário insere o novo valor, o Visual Studio chama [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) no objeto [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) associado ao local.  
  
2. `IDebugProperty2::SetValueAsString` realiza as seguintes tarefas:  
  
   1. Avalia a cadeia de caracteres para produzir um valor.  
  
   2. Associa o objeto [IDebugField](../../extensibility/debugger/reference/idebugfield.md) associado para obter um objeto [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) .  
  
   3. Converte o valor em uma série de bytes.  
  
   4. Chama [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) para colocar os bytes do valor na memória para que o programa que está sendo depurado possa acessá-los.  
  
3. O Visual Studio atualiza a exibição de **locais** (consulte [exibindo locais](../../extensibility/debugger/displaying-locals.md) para obter detalhes).  
  
   Esse procedimento também é usado para alterar o valor de uma variável na janela **Watch** , exceto pelo `IDebugProperty2` objeto associado ao valor do local que é usado em vez do `IDebugProperty2` objeto associado ao próprio local.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Exemplo de implementação de valores de variáveis](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Usa o exemplo MyCEE para percorrer o processo de alteração de valores.  
  
## <a name="see-also"></a>Consulte Também  
 [Escrevendo um avaliador de expressão CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Exibindo locais](../../extensibility/debugger/displaying-locals.md)
