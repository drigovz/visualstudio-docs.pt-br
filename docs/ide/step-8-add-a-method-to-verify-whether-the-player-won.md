---
title: 'Etapa 8: Adicionar um método para verificar se o jogador ganhou'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 6e317f6e-ba4c-4306-8924-300b0c2f65c6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b58cb236f1da88c20e0e96878a7cd5c60052f44f
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118629"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Etapa 8: Adicionar um método para verificar se o jogador ganhou
Você criou um jogo divertido, mas ele precisa de um item adicional para ser finalizado. O jogo deve terminar quando os jogadores ganham, de modo que você precisa adicionar um método `CheckForWinner()` para verificar se o jogador ganhou.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Para adicionar um método para verificar se o jogador ganhou

1. Adicione um método `CheckForWinner()` ao fim do seu código, abaixo do manipulador de eventos `timer1_Tick()`, conforme mostrado no código a seguir.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

     O método usa outro loop `foreach` no Visual C# ou o loop `For Each` no Visual Basic para passar em cada rótulo no <xref:System.Windows.Forms.TableLayoutPanel>. Ele usa o operador de igualdade (`==` no Visual C# e `=` no Visual Basic) para examinar a cor do ícone de cada rótulo e verificar se ela corresponde ao plano de fundo. Se as cores corresponderem, o ícone permanecerá invisível e o jogador não combinou todos os ícones restantes. Nesse caso, o programa usa uma instrução `return` para ignorar o restante do método. Se o loop passar por todos os rótulos sem executar a instrução `return`, isso significa que todos os ícones no formulário foram combinados. O programa mostra uma MessageBox para parabenizar o jogador ganhador e, em seguida, chama o método `Close()` do formulário para encerrar o jogo.

2. Em seguida, o manipulador de eventos <xref:System.Windows.Forms.Control.Click> do rótulo chama o novo método `CheckForWinner()`. Verifique se seu programa busca um ganhador imediatamente depois que ele mostra o segundo ícone que o jogador escolhe. Procure a linha onde você define a cor do segundo ícone escolhido e chame o método `CheckForWinner()` logo depois disso, conforme mostrado no código a seguir.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Salve e execute o programa. Jogue o jogo e combine todos os ícones. Quando você ganha, o programa exibe uma **MessageBox** de congratulação (conforme mostrado na imagem a seguir) e fecha a caixa.

     ![Jogo da memória com MessageBox](../ide/media/express_tut4step8.png)
**Jogo da memória** com **MessageBox**

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, confira [Etapa 9: Experimentar outros recursos](../ide/step-9-try-other-features.md).

- Para retornar à etapa anterior do tutorial, confira [Etapa 7: Manter os pares visíveis](../ide/step-7-keep-pairs-visible.md).
