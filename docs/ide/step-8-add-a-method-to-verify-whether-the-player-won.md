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
ms.openlocfilehash: d53740d0970aba2c5b0442ded722c648f759f724
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575130"
---
# <a name="step-8-add-a-method-to-verify-whether-the-player-won"></a>Etapa 8: Adicionar um método para verificar se o jogador ganhou
Você criou um jogo divertido, mas ele precisa de um item adicional para ser finalizado. O jogo deve terminar quando os jogadores ganham, de modo que você precisa adicionar um método `CheckForWinner()` para verificar se o jogador ganhou.

## <a name="to-add-a-method-to-verify-whether-the-player-won"></a>Para adicionar um método para verificar se o jogador ganhou

1. Adicione um método `CheckForWinner()` ao fim do seu código, abaixo do manipulador de eventos `timer1_Tick()`, conforme mostrado no código a seguir.

     [!code-csharp[VbExpressTutorial4Step8#10](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_1.cs)]
     [!code-vb[VbExpressTutorial4Step8#10](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_1.vb)]

      > [!IMPORTANT]
      > Use o controle linguagem de programação no canto superior direito desta página para exibir o trecho C# de código ou o trecho de código de Visual Basic.<br><br>controle de linguagem ![Programming para Docs.Microsoft.com ](../ide/media/docs-programming-language-control.png)     

     O método usa outro loop de `foreach` C# no loop ou `For Each` no Visual Basic para passar por cada rótulo na <xref:System.Windows.Forms.TableLayoutPanel>. Ele usa o operador de igualdade (`==` C# no e `=` em Visual Basic) para verificar a cor do ícone de cada rótulo para verificar se ele corresponde ao plano de fundo. Se as cores corresponderem, o ícone permanecerá invisível e o jogador não combinou todos os ícones restantes. Nesse caso, o programa usa uma instrução `return` para ignorar o restante do método. Se o loop passar por todos os rótulos sem executar a instrução `return`, isso significa que todos os ícones no formulário foram combinados. O programa mostra uma MessageBox para parabenizar o jogador ganhador e, em seguida, chama o método `Close()` do formulário para encerrar o jogo.

2. Em seguida, o manipulador de eventos <xref:System.Windows.Forms.Control.Click> do rótulo chama o novo método `CheckForWinner()`. Verifique se seu programa busca um ganhador imediatamente depois que ele mostra o segundo ícone que o jogador escolhe. Procure a linha onde você define a cor do segundo ícone escolhido e chame o método `CheckForWinner()` logo depois disso, conforme mostrado no código a seguir.

     [!code-csharp[VbExpressTutorial4Step8#11](../ide/codesnippet/CSharp/step-8-add-a-method-to-verify-whether-the-player-won_2.cs)]
     [!code-vb[VbExpressTutorial4Step8#11](../ide/codesnippet/VisualBasic/step-8-add-a-method-to-verify-whether-the-player-won_2.vb)]

3. Salve e execute o programa. Jogue o jogo e combine todos os ícones. Quando você ganha, o programa exibe uma **MessageBox** de congratulação (conforme mostrado na imagem a seguir) e fecha a caixa.

     ![Jogo da memória com MessageBox](../ide/media/express_tut4step8.png)<br/>
**Jogo da memória** com **MessageBox**

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para acessar a próxima etapa do tutorial, veja [Etapa 9: Experimentar outros recursos](../ide/step-9-try-other-features.md).

- Para retornar à etapa anterior do tutorial, veja [Etapa 7: Manter os pares visíveis](../ide/step-7-keep-pairs-visible.md).
