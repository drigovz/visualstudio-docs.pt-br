---
title: 'Etapa 7: Adicionar problemas de multiplicação e divisão'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64edeb6d6180907e6b1aa07fd5d443e8523c10b1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647469"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Etapa 7: Adicionar problemas de multiplicação e divisão

Na sétima parte deste tutorial, você adicionará problemas de multiplicação e de divisão, mas primeiro pense em como fazer essa alteração. Considere a etapa inicial, que envolve armazenar valores.

> [!NOTE]
> Esse tópico faz parte de uma série de tutoriais sobre conceitos de codificação básica.
> - Para obter uma visão geral do tutorial, confira [Tutorial 2: criar um teste de matemática temporizado](../ide/tutorial-2-create-a-timed-math-quiz.md).
> - Para baixar uma versão completa do código, consulte [exemplo de tutorial de teste de matemática completo](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-add-multiplication-and-division-problems"></a>Para adicionar problemas de multiplicação e de divisão

1. Adicione mais quatro variáveis inteiras ao formulário.

     [!code-vb[VbExpressTutorial3Step7#15](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_1.vb)]
     [!code-csharp[VbExpressTutorial3Step7#15](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_1.cs)]

     [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

2. Como você fez antes, modifique o método de `StartTheQuiz()` para preencher números aleatórios para os problemas de multiplicação e de divisão.

     [!code-vb[VbExpressTutorial3Step7#16](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_2.vb)]
     [!code-csharp[VbExpressTutorial3Step7#16](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_2.cs)]

3. Modifique o método de `CheckTheAnswer()` de modo que ele também verifique os problemas de multiplicação e de divisão.

     [!code-vb[VbExpressTutorial3Step7#17](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_3.vb)]
     [!code-csharp[VbExpressTutorial3Step7#17](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_3.cs)]

     Você não pode inserir facilmente o sinal de multiplicação (×) e o sinal de divisão (÷) usando o C# teclado, portanto, e Visual Basic aceitar um asterisco (*) para multiplicação e uma barra (/) para divisão.

4. Altere a parte a mais recente do manipulador de eventos de escala <xref:System.Windows.Forms.Timer.Tick> do timer de modo que preencha a resposta correta quando o tempo de execução se esgotar.

     [!code-vb[VbExpressTutorial3Step7#23](../ide/codesnippet/VisualBasic/step-7-add-multiplication-and-division-problems_4.vb)]
     [!code-csharp[VbExpressTutorial3Step7#23](../ide/codesnippet/CSharp/step-7-add-multiplication-and-division-problems_4.cs)]

5. Salve e execute seu programa.

     Os participantes de teste devem responder quatro problemas para concluir o teste, conforme mostrado na ilustração.

     ![Teste de matemática com quatro problemas](../ide/media/express_finishedquiz.png)<br/>
***Teste de matemática*** *com quatro problemas*

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, consulte **[Step 8: Customize The Quiz](../ide/step-8-customize-the-quiz.md)** .

- Para retornar à etapa anterior do tutorial, veja [Etapa 6: Adicionar um problema de subtração](../ide/step-6-add-a-subtraction-problem.md).
