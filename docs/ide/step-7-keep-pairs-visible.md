---
title: 'Etapa 7: Manter os pares visíveis'
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.assetid: 42e1d08c-7b2e-4efd-9f47-85d6206afe35
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d0216d778278f02f7fc63630f4ff6ce90c755e3c
ms.sourcegitcommit: 6eed0372976c0167b9a6d42ba443f9a474b8bb91
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71118651"
---
# <a name="step-7-keep-pairs-visible"></a>Etapa 7: Manter os pares visíveis
O jogo funciona bem, desde que o jogador escolha apenas pares de ícones que não correspondam. Porém, considere o que deve acontecer quando o jogador escolher um par correspondente. Em vez de fazer os ícones desaparecerem ativando o temporizador (usando o método <xref:System.Windows.Forms.Timer.Start>), o jogo deve redefinir a si próprio para que ele não acompanhe mais nenhum rótulo usando as variáveis de referência `firstClicked` e `secondClicked`, sem redefinir as cores dos dois rótulos que foram escolhidos.

## <a name="to-keep-pairs-visible"></a>Para manter os pares visíveis

1. Adicione a instrução `if` a seguir ao método do manipulador de eventos `label_Click()`, próximo do fim do código, logo acima da instrução onde você inicia o temporizador. Observe mais detalhadamente o código enquanto o adiciona ao programa. Leve em consideração como o código funciona.

     [!code-csharp[VbExpressTutorial4Step7#9](../ide/codesnippet/CSharp/step-7-keep-pairs-visible_1.cs)]
     [!code-vb[VbExpressTutorial4Step7#9](../ide/codesnippet/VisualBasic/step-7-keep-pairs-visible_1.vb)]

     A primeira linha da instrução `if` que você acabou de adicionar verifica se o ícone no primeiro rótulo que o jogador escolhe é igual ao ícone no segundo rótulo. Se os ícones forem idênticos, o programa executará as três instruções entre as chaves no C# ou as três instruções na instrução `if` do Visual Basic. As primeiras duas instruções redefinem as variáveis de referência `firstClicked` e `secondClicked` para que elas não acompanhem mais nenhum dos rótulos. (Você pode reconhecer essas duas instruções do manipulador de eventos <xref:System.Windows.Forms.Timer.Tick> do temporizador). A terceira instrução é uma instrução `return`, que orienta o programa a pular o restante das instruções no método sem executá-las.

     Se estiver programando no Visual C#, você deve ter percebido que alguns dos códigos usam um único sinal de igual (`=`), enquanto outras instruções usam dois sinais de igual (`==`). Leve em consideração por que `=` é usado em alguns locais, mas `==` é usado em outros.

     Esse é um bom exemplo que mostra a diferença. Observe atentamente o código entre os parênteses na instrução `if`.

    ```vb
    firstClicked.Text = secondClicked.Text
    ```

    ```csharp
    firstClicked.Text == secondClicked.Text
    ```

     Em seguida, observe atentamente a primeira instrução no bloco de código após a instrução `if`.

    ```vb
    firstClicked = Nothing
    ```

    ```csharp
    firstClicked = null;
    ```

     A primeira dessas duas instruções verifica se dois ícones são iguais. Como dois valores estão sendo comparados, o programa Visual C# usa o operador de igualdade `==`. A segunda instrução realmente altera o valor (chamado *atribuição*), definindo a variável de referência `firstClicked` igual a `null` para redefini-la. Por esse motivo, ela usa o operador de atribuição `=` no lugar. O Visual C# usa `=` para definir valores e `==` para compará-los. O Visual Basic usa `=` para atribuição de variável e comparação.

2. Salve e execute o programa e, em seguida, comece a escolher os ícones no formulário. Se você escolher um par que não corresponda, o evento Tick do temporizador é disparado e ambos os ícones desaparecem. Se você escolher um par correspondente, a nova instrução `if` será executada e a instrução de retorno fará com que o método pule o código que inicia o temporizador, de modo que o ícone permanece visível, conforme mostrado na imagem a seguir.

     ![Jogo que você cria neste tutorial](../ide/media/express_finishedgame.png)
**Jogo da memória** com pares de ícone visíveis

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, confira [Etapa 8: Adicionar um método para verificar se o jogador ganhou](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

- Para retornar à etapa anterior do tutorial, confira [Etapa 6: Adicionar um temporizador](../ide/step-6-add-a-timer.md).
