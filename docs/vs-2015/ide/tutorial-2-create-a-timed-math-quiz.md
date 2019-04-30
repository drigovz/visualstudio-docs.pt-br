---
title: 'Tutorial 2: Criar um teste de matemática temporizado | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d7165d08-ace3-457d-b57d-fb8f80760a6f
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2a87a192f7a14a4d59a5ca5cff15bc62abbdefc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443284"
---
# <a name="tutorial-2-create-a-timed-math-quiz"></a>Tutorial 2: Criar um teste de matemática temporizado
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Neste tutorial, você cria um teste no qual o tomador de teste deve responder a quatro problemas aritméticos aleatórios dentro de um tempo especificado. Você aprenderá como:  
  
- Gere números aleatórios usando a classe de `Random`.  
  
- Disparar eventos para que ocorram em um horário específico usando um controle de **Temporizador**.  
  
- Fluxo do programa de controle usando instruções de `if else`.  
  
- Execute operações aritméticas básicas no código.  
  
  Quando você terminar, seu teste ficará parecido com a imagem a seguir, mas com números diferentes.  
  
  ![Teste de matemática com quatro problemas](../ide/media/express-finishedquiz.png "Express_FinishedQuiz")  
  Teste que você cria neste tutorial  
  
  Para baixar uma versão concluída do teste, consulte [Exemplo de tutorial de teste completo de matemática](http://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).  
  
> [!NOTE]
> O Visual C# e o Visual Basic são abordados neste tutorial, por isso, concentre-se nas informações específicas da linguagem de programação que você está usando.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Etapa 1: Criar um projeto e adicionar rótulos ao formulário](../ide/step-1-create-a-project-and-add-labels-to-your-form.md)|Comece criando o projeto, alterando propriedades e adicionando controles `Label`.|  
|[Etapa 2: Criar um problema de adição aleatório](../ide/step-2-create-a-random-addition-problem.md)|Crie um problema de adição, e use a classe de `Random` para gerar números aleatórios.|  
|[Etapa 3: Adicionar um temporizador de contagem regressiva](../ide/step-3-add-a-countdown-timer.md)|Adicione um timer de contagem regressiva de modo que o teste possa ser cronometrado.|  
|[Etapa 4: Adicionar o método CheckTheAnswer()](../ide/step-4-add-the-checktheanswer-parens-method.md)|Adicione um método para verificar se o comprador de teste inseriu uma resposta correta para o problema.|  
|[Etapa 5: Adicionar manipuladores de eventos de inserção aos controles NumericUpDown](../ide/step-5-add-enter-event-handlers-for-the-numericupdown-controls.md)|Adicione manipuladores de eventos que facilitam a tomada do teste.|  
|[Etapa 6: Adicionar um problema de subtração](../ide/step-6-add-a-subtraction-problem.md)|Adicione um problema de subtração que gerencia números aleatórios, usa o timer, e o verifica se as respostas estão corretas.|  
|[Etapa 7: Adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md)|Adicione problemas de divisão e multiplicação que geram números aleatórios, usam o timer, e verificam se as respostas estão corretas.|  
|[Etapa 8: Personalizar o teste](../ide/step-8-customize-the-quiz.md)|Tente outros recursos, como alterar cores e adicionar uma dica.|
