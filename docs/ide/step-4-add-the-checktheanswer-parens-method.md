---
title: 'Etapa 4: Adicionar o método CheckTheAnswer()'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- CSharp
- VB
ms.assetid: c66f3831-b4a0-40bc-a109-8f46f4db35ed
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4c940893f74697bdbf51c5910e08e925fedf26db
ms.sourcegitcommit: 541a0556958201ad6626bc8638406ad02640f764
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71079408"
---
# <a name="step-4-add-the-checktheanswer-method"></a>Etapa 4: Adicionar o método CheckTheAnswer()

Na primeira parte deste tutorial, você irá escrever um método, `CheckTheAnswer()`, que determina se as respostas para os problemas de matemática estão corretas. Esse tópico faz parte de uma série de tutoriais sobre conceitos de codificação básica. Para obter uma visão geral do tutorial, confira [Tutorial 2: Criar um teste de matemática temporizado](../ide/tutorial-2-create-a-timed-math-quiz.md).

> [!NOTE]
> Esse tópico faz parte de uma série de tutoriais sobre conceitos de codificação básica.
> - Para obter uma visão geral do tutorial, confira [Tutorial 2: Criar um teste de matemática temporizado](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Para baixar uma versão completa do código, consulte [exemplo de tutorial de teste de matemática completo](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-verify-whether-the-answers-are-correct"></a>Para verificar se as respostas estão corretas

> [!NOTE]
> Se você estiver seguindo o Visual Basic, você usará a palavra-chave de `Function` em vez da palavra-chave comum de `Sub` porque esse método retorna um valor. É realmente simples: um sub não retorna um valor, mas uma função sim.

1. Adicione o método `CheckTheAnswer()`.

     Quando esse método é chamado, ele adiciona os valores de addend1 e addend2 e compara o resultado com o valor no controle <xref:System.Windows.Forms.NumericUpDown> de soma. Se os valores forem iguais, o método retornará um valor de `true`. Caso contrário, o método retorna um valor de `false`. Seu código deve se parecer com o seguinte.

     [!code-vb[VbExpressTutorial3Step4#8](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_1.vb)]
     [!code-csharp[VbExpressTutorial3Step4#8](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_1.cs)]

     > [!IMPORTANT]
     > Use o controle linguagem de programação no canto superior direito desta página para exibir o trecho C# de código ou o trecho de código de Visual Basic.<br><br>![Controle de linguagem de programação para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     Em seguida, verifique a resposta atualizando o código no método do manipulador de eventos <xref:System.Windows.Forms.Timer.Tick> do timer para chamar o novo método `CheckTheAnswer()`.

2. Adicione o seguinte código à instrução `if else`.

     [!code-vb[VbExpressTutorial3Step4#10](../ide/codesnippet/VisualBasic/step-4-add-the-checktheanswer-parens-method_2.vb)]
     [!code-csharp[VbExpressTutorial3Step4#10](../ide/codesnippet/CSharp/step-4-add-the-checktheanswer-parens-method_2.cs)]

     Se a resposta estiver correta, `CheckTheAnswer()` retornará `true`. O manipulador de eventos para o temporizador, mostra uma mensagem congratulatória e disponibiliza novamente o botão **Iniciar**. Caso contrário, o teste continua.

3. Salve seu programa, execute-o, inicie um teste e forneça uma resposta correta ao problema de adição.

    > [!NOTE]
    > Ao inserir sua resposta, você deve ou selecione o valor padrão antes de começar a inserir sua resposta ou excluir o zero manualmente. Você corrigirá esse comportamento mais tarde neste tutorial.

     Quando você fornece uma resposta correta, uma caixa de mensagem abre, o botão **Iniciar** fica disponível e o temporizador para.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, **consulte [Step 5: Adicione manipuladores de eventos de entrada para os](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)controles**NumericUpDown.

- Para retornar à etapa anterior do tutorial, confira [Etapa 3: Adicionar um temporizador de contagem regressiva](../ide/step-3-add-a-countdown-timer.md).
