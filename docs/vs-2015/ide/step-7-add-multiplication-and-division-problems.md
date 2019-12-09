---
title: 'Etapa 7: adicionar problemas de multiplicação e divisão | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: e638959e-f6a4-4eb4-b2e9-f63b7855cf8f
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7f7efb0acf6611346abe67a7a94e5c221919665
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646973"
---
# <a name="step-7-add-multiplication-and-division-problems"></a>Etapa 7: Adicionar problemas de multiplicação e divisão
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na sétima parte deste tutorial, você adicionará problemas de multiplicação e de divisão, mas primeiro pense em como fazer essa alteração. Considere a etapa inicial, que envolve armazenar valores.

### <a name="to-add-multiplication-and-division-problems"></a>Para adicionar problemas de multiplicação e de divisão

1. Adicione mais quatro variáveis inteiras ao formulário.

     [!code-csharp[VbExpressTutorial3Step7#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial3Step7#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#15)]

2. Como você fez antes, modifique o método de `StartTheQuiz()` para preencher números aleatórios para os problemas de multiplicação e de divisão.

     [!code-csharp[VbExpressTutorial3Step7#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial3Step7#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#16)]

3. Modifique o método de `CheckTheAnswer()` de modo que ele também verifique os problemas de multiplicação e de divisão.

     [!code-csharp[VbExpressTutorial3Step7#17](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#17)]
     [!code-vb[VbExpressTutorial3Step7#17](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#17)]

     Não é possível inserir facilmente o sinal de multiplicação (×) e o sinal de divisão (÷) usando o teclado, então o Visual C# e o Visual Basic aceitam um asterisco (*) para multiplicação e uma barra (/) para divisão.

4. Altere a parte a mais recente do manipulador de eventos de escala do timer de modo que preencha a resposta correta quando o tempo de execução se esgotar.

     [!code-csharp[VbExpressTutorial3Step7#23](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial3step7/cs/form1.cs#23)]
     [!code-vb[VbExpressTutorial3Step7#23](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial3step7/vb/form1.vb#23)]

5. Salve e execute seu programa.

     Os participantes de teste devem responder quatro problemas para concluir o teste, conforme mostrado na ilustração.

     ![Teste de matemática com quatro problemas](../ide/media/express-finishedquiz.png "Express_FinishedQuiz") Teste de matemática com quatro problemas

### <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, consulte [Etapa 8: personalizar o teste](../ide/step-8-customize-the-quiz.md).

- Para retornar à etapa anterior do tutorial, consulte [Etapa 6: adicionar um problema de subtração](../ide/step-6-add-a-subtraction-problem.md).
