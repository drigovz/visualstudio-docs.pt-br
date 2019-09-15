---
title: 'Etapa 8: Personalizar o teste'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b68d46ad5c585dca9fd48f39a2e47ac95f5a11c8
ms.sourcegitcommit: 0e482cfc15f809b564c3de61646f29ecd7bfcba6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70987853"
---
# <a name="step-8-customize-the-quiz"></a>Etapa 8: Personalizar o teste

Na última parte do tutorial, você explorará algumas maneiras de personalizar o questionário e expandir no que já aprendeu. Por exemplo, pense em como o programa cria os problemas aleatórios de divisão para os quais a resposta nunca é uma fração. Para obter mais informações, mude o controle `timeLabel` para uma cor diferente e dê uma dica à pessoa realizando o teste.

> [!NOTE]
> Esse tópico faz parte de uma série de tutoriais sobre conceitos de codificação básica. 
> - Para obter uma visão geral do tutorial, confira [Tutorial 2: Criar um teste de matemática temporizado](../ide/tutorial-2-create-a-timed-math-quiz.md). 
> - Para baixar uma versão completa do código, consulte [exemplo de tutorial de teste de matemática completo](https://code.msdn.microsoft.com/Complete-Math-Quiz-8581813c).

## <a name="to-customize-the-quiz"></a>Para personalizar o teste

- Quando apenas cinco segundos permanecem em um teste, transforme o controle de **rótulo** de marca em vermelho definindo sua propriedade **BackColor** .

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  > [!IMPORTANT]
  > Use o controle linguagem de programação no canto superior direito desta página para exibir o trecho C# de código ou o trecho de código de Visual Basic.<br><br>![Controle de linguagem de programação para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  Redefina a cor quando o teste acabar.

- Dê ao comprador de teste uma dica executando um som quando a resposta correta for inserida em um controle <xref:System.Windows.Forms.NumericUpDown>. (Você deve escrever um manipulador de eventos para o evento <xref:System.Windows.Forms.NumericUpDown.ValueChanged> de cada controle, que será acionado sempre que o comprador de teste alterar o valor do controle.)

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para o próximo tutorial, consulte  **[o tutorial 3: Crie um jogo](../ide/tutorial-3-create-a-matching-game.md)** correspondente.

- Para retornar à etapa anterior do tutorial, confira [Etapa 7: Adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md).
