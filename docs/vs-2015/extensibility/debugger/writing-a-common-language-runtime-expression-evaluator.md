---
title: Escrevendo um avaliador de expressão Common Language Runtime | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 961a4d646a61fedda381f9451902b3bcdcc956d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838595"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escrevendo um avaliador de expressão do Common Language Runtime
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!IMPORTANT]
> No Visual Studio 2015, essa maneira de implementar avaliadores de expressão é preterida. Para obter informações sobre como implementar avaliadores de expressão CLR, consulte os [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [exemplo de avaliador de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 O avaliador de expressão (EE) é a parte de um mecanismo de depuração (DE) que manipula a sintaxe e a semântica da linguagem de programação que produziu o código que está sendo depurado. As expressões devem ser avaliadas no contexto de uma linguagem de programação. Por exemplo, em alguns idiomas, a expressão "a + B" significa "a soma de A e B". Em outros idiomas, a mesma expressão pode significar "A ou B". Portanto, um EE separado deve ser escrito para cada linguagem de programação que gera código de objeto a ser depurado no IDE do Visual Studio.  
  
 Alguns aspectos do pacote de depuração do Visual Studio devem interpretar o código no contexto da linguagem de programação. Por exemplo, quando a execução é interrompida em um ponto de interrupção, todas as expressões que o usuário tiver digitado em uma janela de **inspeção** devem ser avaliadas e exibidas. Além disso, o usuário pode alterar o valor de uma variável local digitando uma expressão em uma janela de **inspeção** ou na janela **imediata** .  
  
## <a name="in-this-section"></a>Nesta seção  
 [Common Language Runtime e avaliação de expressão](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md)  
 Explica que quando você está integrando a linguagem de programação proprietária no IDE do Visual Studio, escrever um EE capaz de avaliar expressões dentro do contexto da linguagem proprietária permite que você compile para uma MSIL (Microsoft Intermediate Language) sem escrever um mecanismo de depuração.  
  
 [Arquitetura do avaliador de expressão](../../extensibility/debugger/expression-evaluator-architecture.md)  
 Discute como implementar as interfaces de EE necessárias e chamar o provedor de símbolo de Common Language Runtime (SP) e as interfaces de fichário.  
  
 [Registrando um avaliador de expressão](../../extensibility/debugger/registering-an-expression-evaluator.md)  
 Observa que o EE deve se registrar como uma fábrica de classes com os ambientes de tempo de execução do Common Language Runtime e do Visual Studio.  
  
 [Implementando um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md)  
 Descreve como o processo de avaliação de uma expressão inclui o mecanismo de depuração (DE), o provedor de símbolos (SP), o objeto de fichário e o avaliador de expressão (EE).  
  
 [Exibindo locais](../../extensibility/debugger/displaying-locals.md)  
 Descreve como, quando a execução pausa, o pacote de depuração chama o DE para obter uma lista de variáveis e argumentos locais.  
  
 [Avaliando uma expressão da janela Inspeção](../../extensibility/debugger/evaluating-a-watch-window-expression.md)  
 Documenta como o pacote de depuração do Visual Studio chama de DE para determinar o valor atual de cada expressão em sua lista de observação.  
  
 [Alterando o valor de um local](../../extensibility/debugger/changing-the-value-of-a-local.md)  
 Explica que, ao alterar o valor de um local, cada linha da janela locais tem um objeto associado que fornece o nome, o tipo e o valor atual de um local.  
  
 [Implementando visualizadores de tipo e visualizadores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md)  
 Explica qual interface precisa ser implementada por qual componente para dar suporte a visualizadores de tipo e espectadores personalizados.  
  
## <a name="see-also"></a>Consulte Também  
 [Extensibilidade do depurador do Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
