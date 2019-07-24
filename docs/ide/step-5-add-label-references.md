---
title: 'Etapa 5: Adicionar referências de rótulo'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- csharp
- vb
ms.assetid: d418350c-0396-494e-8149-71fa61b395c5
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e35224529e556afee673aafa8e5e8b68e61157f7
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/23/2019
ms.locfileid: "68416571"
---
# <a name="step-5-add-label-references"></a>Etapa 5: Adicionar referências de rótulo
O programa precisa rastrear quais controles de rótulo o jogador escolhe. Atualmente, o programa mostra todos os rótulos escolhidos pelo jogador. Mas isso será alterado. Depois que o primeiro rótulo é escolhido, o programa deve mostrar o ícone do rótulo. Depois que o segundo rótulo é escolhido, o programa deve exibir ambos os ícones por um breve momento e depois ocultá-los novamente. Agora seu programa rastreará qual controle de rótulo será escolhido primeiro e qual será escolhido em segundo usando *variáveis de referência*.

## <a name="to-add-label-references"></a>Para adicionar referências de rótulo

1. Adicione referências de rótulo ao seu formulário usando o código a seguir.

     [!code-vb[VbExpressTutorial4Step5#5](../ide/codesnippet/VisualBasic/step-5-add-label-references_1.vb)]
     [!code-csharp[VbExpressTutorial4Step5#5](../ide/codesnippet/CSharp/step-5-add-label-references_1.cs)]

     Essas variáveis de referência parecem semelhantes às instruções que você usou anteriormente para adicionar objetos (como os objetos <xref:System.Windows.Forms.Timer>, <xref:System.Collections.Generic.List%601> e <xref:System.Random>) ao formulário. No entanto, essas instruções não fazem com que os dois controles de rótulo extras apareçam no formulário, pois a palavra-chave `new` não foi usada em nenhuma das duas instruções. Sem a palavra-chave `new`, nenhum objeto é criado. É por isso que `firstClicked` e `secondClicked` são chamadas de variáveis de referência: Elas apenas acompanham (ou se referem a) os objetos de rótulo.

     Quando uma variável não estiver rastreando um objeto, ela será definida para um valor reservado especial: `null` no Visual C# e `Nothing` no Visual Basic. Desse modo, quando o programa for iniciado, `firstClicked` e `secondClicked` serão definidas como `null` ou `Nothing`, o que significa que as variáveis não estão rastreando nada.

2. Modifique o manipulador de eventos <xref:System.Windows.Forms.Control.Click> para usar a nova variável de referência `firstClicked`. Remova a última instrução no método do manipulador de eventos `label_Click()` (`clickedLabel.ForeColor = Color.Black;`) e substitua-a pela instrução `if` que se segue. (Não se esqueça de incluir o comentário e a instrução `if` inteira.)

     [!code-vb[VbExpressTutorial4Step5#6](../ide/codesnippet/VisualBasic/step-5-add-label-references_2.vb)]
     [!code-csharp[VbExpressTutorial4Step5#6](../ide/codesnippet/CSharp/step-5-add-label-references_2.cs)]

3. Salve e execute seu programa. Escolha um dos controles de rótulo e seu ícone é exibido.

4. Escolha o próximo controle de rótulo e observe que nada acontece. O programa já está rastreando o primeiro rótulo que o jogador escolheu, de modo que `firstClicked` não é igual a `null` no Visual C# ou `Nothing` no Visual Basic. Quando sua instrução `if` verifica `firstClicked` para determinar se ele é igual a `null` ou `Nothing`, ela descobre que não é e não executa as instruções na instrução `if`. Desse modo, somente o primeiro ícone que é escolhido torna-se preto e os outros ícones ficam invisíveis, conforme mostrado na imagem a seguir.

     ![Jogo da memória mostrando um ícone](../ide/media/express_tut4step5.png)
**Jogo da memória** mostrando um ícone

     Essa situação será corrigida na primeira etapa do tutorial adicionando um controle **Temporizador**.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, confira [Etapa 6: Adicionar um temporizador](../ide/step-6-add-a-timer.md).

- Para retornar à etapa anterior do tutorial, confira [Etapa 4: Adicionar um manipulador de eventos de clique a cada rótulo](../ide/step-4-add-a-click-event-handler-to-each-label.md).
