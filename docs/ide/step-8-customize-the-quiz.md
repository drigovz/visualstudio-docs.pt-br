---
title: 'Etapa 8: Personalizar o teste'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: dc8edb13-1b23-47d7-b859-8c6f7888c1a9
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e568a9fa844802ddab934264cbc316d3514fe577
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579375"
---
# <a name="step-8-customize-the-quiz"></a>Etapa 8: Personalizar o teste

Na última parte do tutorial, você explorará algumas maneiras de personalizar o questionário e expandir no que já aprendeu. Por exemplo, pense em como o programa cria os problemas aleatórios de divisão para os quais a resposta nunca é uma fração. Para obter mais informações, mude o controle `timeLabel` para uma cor diferente e dê uma dica à pessoa realizando o teste.

> [!NOTE]
> Esse tópico faz parte de uma série de tutoriais sobre conceitos de codificação básica. Para uma visão geral do tutorial, consulte [Tutorial 2: Crie um teste de matemática cronometrado](../ide/tutorial-2-create-a-timed-math-quiz.md).

## <a name="to-customize-the-quiz"></a>Para personalizar o teste

- Quando apenas cinco segundos permanecerem em um teste, gire o controle **timeLabel** vermelho definindo sua propriedade **BackColor.**

  ```csharp
  timeLabel.BackColor = Color.Red;
  ```

  ```vb
  timeLabel.BackColor = Color.Red
  ```

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  Redefina a cor quando o teste acabar.

- Dê ao comprador de teste uma dica executando um som quando a resposta correta for inserida em um controle <xref:System.Windows.Forms.NumericUpDown>. (Você deve escrever um manipulador de eventos para o evento <xref:System.Windows.Forms.NumericUpDown.ValueChanged> de cada controle, que será acionado sempre que o comprador de teste alterar o valor do controle.)

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir ao próximo tutorial, consulte **[Tutorial 3: Crie um jogo de correspondência](../ide/tutorial-3-create-a-matching-game.md)**.

- Para retornar à etapa tutorial anterior, consulte [Passo 7: Adicionar problemas de multiplicação e divisão](../ide/step-7-add-multiplication-and-division-problems.md).
