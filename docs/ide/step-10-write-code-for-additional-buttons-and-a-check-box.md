---
title: 'Etapa 10: Escrever código para botões adicionais e uma caixa de seleção'
ms.date: 08/30/2019
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9763026a4ef1c219bcb9f5b5270ac5d3b48e2e14
ms.sourcegitcommit: 4dfe098ac0df294aad63e6b384d6575980798ca3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70887873"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Etapa 10: Escrever código para botões adicionais e uma caixa de seleção

Agora você está pronto para concluir os outros quatro métodos. Você pode copiar e colar esse código, mas se deseja saber a maioria deste tutorial, digite o código e use o IntelliSense.

Este código adiciona funcionalidades aos botões que você adicionou anteriormente. Sem esse código, os botões não fazem nada. Os botões usam o código em seus eventos de <xref:System.Windows.Forms.Control.Click> (e na caixa de seleção usa o evento de <xref:System.Windows.Forms.CheckBox.CheckedChanged>) para fazer coisas diferentes quando você ativa os controles. Por exemplo, o `clearButton_Click` evento ( `ClearButton_Click`ou), que é ativado quando você escolhe o botão **limpar imagem** , apaga a imagem atual definindo sua propriedade **Image** como **NULL** (ou, **Nothing**). Cada evento no código inclui comentários que explicam o que o código faz.

> [!TIP]
> Como uma melhor prática: Sempre comente o seu código. Os comentários são informações para uma pessoa ler e vale a pena tornar seu código mais legível. Tudo em uma linha de comentário é ignorado pelo aplicativo. No C#, você comenta uma linha digitando duas barras no início (//) e, no Visual Basic você comenta uma linha, começando com uma aspa simples (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Como escrever código para botões adicionais e uma caixa de seleção

Adicione o seguinte código ao seu arquivo de código **Form1** (*Form1.cs* ou *Form1.vb*).
> [!IMPORTANT]
> Use o controle linguagem de programação no canto superior direito desta página para exibir o trecho C# de código ou o trecho de código de Visual Basic.<br><br>![Controle de linguagem de programação para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, **consulte [a etapa 11: Execute seu aplicativo e tente outros recursos](../ide/step-11-run-your-program-and-try-other-features.md).**

* Para retornar à etapa anterior do tutorial, confira [Etapa 9: Examinar, comentar e testar o código](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Consulte também

* [Tutorial 2: Criar um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Criar um jogo de correspondência](tutorial-3-create-a-matching-game.md)
