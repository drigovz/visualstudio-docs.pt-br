---
title: Escrever código para botões adicionais e uma caixa de seleção
description: Saiba como escrever código para botões adicionais e uma caixa de cheeck no tutorial criar um visualizador de imagem.
ms.date: 08/30/2019
ms.custom: SEO-VS-2020
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d66f7705821025bd5e30ea0d0c7f2dd57d540e4
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189896"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Etapa 10: Escrever código para botões adicionais e uma caixa de seleção

Agora você está pronto para concluir os outros quatro métodos. Você pode copiar e colar esse código, mas se deseja saber a maioria deste tutorial, digite o código e use o IntelliSense.

Este código adiciona funcionalidades aos botões que você adicionou anteriormente. Sem esse código, os botões não fazem nada. Os botões usam o código em seus eventos de <xref:System.Windows.Forms.Control.Click> (e na caixa de seleção usa o evento de <xref:System.Windows.Forms.CheckBox.CheckedChanged>) para fazer coisas diferentes quando você ativa os controles. Por exemplo, o `clearButton_Click` evento ( `ClearButton_Click` ou), que é ativado quando você escolhe o **botão limpar imagem** , apaga a imagem atual definindo sua propriedade **Image** como **NULL** (ou, **Nothing**). Cada evento no código inclui comentários que explicam o que o código faz.

> [!TIP]
> Como prática recomendada: Comente sempre o seu código. Os comentários são informações para uma pessoa ler e vale a pena tornar seu código mais legível. Tudo em uma linha de comentário é ignorado pelo aplicativo. Em C#, você comenta uma linha digitando duas barras no início (//) e, em Visual Basic você comenta uma linha, começando com uma aspa simples (').

## <a name="how-to-write-code-for-additional-buttons-and-a-check-box"></a>Como escrever código para botões adicionais e uma caixa de seleção

Adicione o seguinte código ao seu arquivo de código **Form1** (*Form1.cs* ou *Form1.vb*).

  [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

  [!code-csharp[VbExpressTutorial1Step9_10#2](../ide/codesnippet/CSharp/step-10-write-code-for-additional-buttons-and-a-check-box_1.cs)]

  [!code-vb[VbExpressTutorial1Step9_10#2](../ide/codesnippet/VisualBasic/step-10-write-code-for-additional-buttons-and-a-check-box_1.vb)]

> [!NOTE]
> Seu código pode não exibir as letras "camelCase".

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[etapa 11: executar seu aplicativo e experimentar outros recursos](../ide/step-11-run-your-program-and-try-other-features.md)**.

* Para retornar à etapa anterior do tutorial, veja [Etapa 9: Revisar, comentar e testar o código](../ide/step-9-review-comment-and-test-your-code.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: criar um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: criar um jogo de correspondência](tutorial-3-create-a-matching-game.md)
