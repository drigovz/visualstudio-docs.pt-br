---
title: Escrevendo um avaliador de expressão em tempo de execução de linguagem comum | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- expression evaluators, tutorial
- expression evaluation, samples
- debugging [Debugging SDK], expression evaluators tutorial
ms.assetid: bd79d57f-8e0a-4e14-a417-0b1de28fa1b2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4e46eaef395a7c66792662b3c5d4b9fbad419dfb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712318"
---
# <a name="writing-a-common-language-runtime-expression-evaluator"></a>Escrevendo um avaliador de expressão em tempo de execução de linguagem comum
> [!IMPORTANT]
> No Visual Studio 2015, essa forma de implementar avaliadores de expressão é preterida. Para obter informações sobre a implementação de avaliadores de expressão CLR, consulte [avaliadores de expressão CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [amostra avaliadora de expressão gerenciada](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 O avaliador de expressão (EE) é a parte de um mecanismo de depuração (DE) que lida com a sintaxe e semântica da linguagem de programação que produziu o código sendo depurado. As expressões devem ser avaliadas no contexto de uma linguagem de programação. Por exemplo, em algumas línguas, a expressão "A+B" significa "a soma de A e B". Em outras línguas, a mesma expressão pode significar "A ou B". Assim, um EE separado deve ser escrito para cada linguagem de programação que gera código de objeto a ser depurado no Visual Studio IDE.

 Alguns aspectos do pacote de depuração do Visual Studio devem interpretar o código no contexto da linguagem de programação. Por exemplo, quando a execução é interrompida em um ponto de interrupção, todas as expressões digitadas pelo usuário em uma janela **do relógio** devem ser avaliadas e exibidas. O usuário pode alterar o valor de uma variável local digitando uma expressão em uma janela **do relógio** ou na janela **Imediata.**

## <a name="in-this-section"></a>Nesta seção
 [Avaliação de tempo de execução e expressão de linguagem comum](../../extensibility/debugger/common-language-runtime-and-expression-evaluation.md) Explica que quando você está integrando a linguagem de programação proprietária no Visual Studio IDE, escrever um EE capaz de avaliar expressões dentro do contexto da linguagem proprietária permite que você compile para uma linguagem intermediária da Microsoft (MSIL) sem escrever um mecanismo de depuração.

 [Arquitetura avaliadora de expressão](../../extensibility/debugger/expression-evaluator-architecture.md) Discute como implementar as interfaces EE necessárias e chamar o provedor de símbolos de tempo de execução (SP) e interfaces de aglutinamento de idiomas comuns.

 [Registre um avaliador de expressão](../../extensibility/debugger/registering-an-expression-evaluator.md) Observa que o EE deve registrar-se como uma fábrica de classes com o tempo de execução do idioma comum e ambientes de tempo de execução do Visual Studio.

 [Implementar um avaliador de expressão](../../extensibility/debugger/implementing-an-expression-evaluator.md) Descreve como o processo de avaliação de uma expressão inclui o mecanismo de depuração (DE), o provedor de símbolos (SP), o objeto de aglutinante e o avaliador de expressão (EE).

 [Mostrar locais](../../extensibility/debugger/displaying-locals.md) Descreve como, quando a execução é pausada, o pacote de depuração chama o DE para obter uma lista de variáveis e argumentos locais.

 [Avalie a expressão da janela do relógio](../../extensibility/debugger/evaluating-a-watch-window-expression.md) Documenta como o pacote de depuração do Visual Studio chama o DE para determinar o valor atual de cada expressão em sua lista de observação.

 [Alterar o valor de um local](../../extensibility/debugger/changing-the-value-of-a-local.md) Explica que ao alterar o valor de um local, cada linha da janela Locals possui um objeto associado que fornece o nome, o tipo e o valor atual de um local.

 [Implementar visualizadores de tipo e visualizadores personalizados](../../extensibility/debugger/implementing-type-visualizers-and-custom-viewers.md) Explica qual interface precisa ser implementada por qual componente suportar visualizadores de tipo e visualizadores personalizados.

## <a name="see-also"></a>Confira também
 [Extensibilidade do depurador visual studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
