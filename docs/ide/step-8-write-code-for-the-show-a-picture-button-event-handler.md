---
title: 'Etapa 8: Escrever código para o manipulador de eventos do botão Mostrar uma Imagem'
ms.date: 08/30/2019
ms.assetid: 07f4ec00-cda4-42f4-98bb-37edc7167de7
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
ms.openlocfilehash: d74c9ecda0e3ab23c1f2ab1cb2180a60701c069a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579813"
---
# <a name="step-8-write-code-for-the-show-a-picture-button-event-handler"></a>Etapa 8: Escrever código para o manipulador de eventos do botão Mostrar uma Imagem

Nesta etapa, você faz o Mostrar um botão **de imagem** funcionar da seguinte forma:

- Quando um usuário escolhe esse botão, <xref:System.Windows.Forms.OpenFileDialog> o aplicativo abre uma caixa.

- Se um usuário abrir um arquivo de imagem, o aplicativo mostrará essa imagem no <xref:System.Windows.Forms.PictureBox>.

O IDE tem uma ferramenta poderosa chamada IntelliSense que ajuda você a gravar código. À medida que você digita código, o IDE abre uma caixa com conclusões sugeridas para palavras parciais que você digita.

O IntelliSense tenta determinar o que você quer fazer a seguir e pula automaticamente para o último item escolhido na lista. Você pode usar as setas para cima ou para abaixo para mover na lista, ou continuar digitando letras para refinar as opções. Ao ver a opção que deseja, escolha a tecla **Tab** para selecioná-la. Ou, você pode ignorar as sugestões, se não forem necessárias.

## <a name="to-write-code-for-the-show-a-picture-button-event-handler"></a>Para escrever código para o manipulador de eventos do botão Mostrar uma imagem

1. Acesse o **Designer de Formulários do Windows** e clique duas vezes no botão **Mostrar uma imagem**. O IDE imediatamente vai para o designer de código e move `showButton_Click()` o cursor para que ele esteja dentro do método (alternativamente), `ShowButton_Click()`que você adicionou anteriormente.

1. Digite um `i` na linha vazia entre as duas chaves `{ }`. (No Visual Basic, digite `Private Sub...` na `End Sub`linha vazia entre e .) Uma janela **IntelliSense** é aberta, como mostrado na imagem a seguir.

    ![IntelliSense com o código do Visual C&#35;](../ide/media/express_ifintellisense.png)

    > [!NOTE]
    > Seu código pode não exibir manipuladores de eventos em letras "camelCase".

1. A janela **IntelliSense** deve `if`destacar a palavra . (Se não, digite `f`uma minúscula , e ele vai.) Observe como uma caixa *de dica de ferramenta* ao lado da janela **IntelliSense** aparece com a descrição, **código de trecho para se a declaração**. (No Visual Basic, a dica de ferramenta também afirma que este é um trecho, mas com uma redação ligeiramente diferente.) Você deseja usar esse trecho, então escolha a `if` **tecla Tab** para inserir em seu código. Em seguida, pressione a tecla **Tab** novamente para usar o snippet `if`. (Se você pressionou outro item e sua janela do **IntelliSense** desapareceu, apague `i` e o digite novamente, e a janela do **IntelliSense** será reaberta).

    ![Código do Visual C&#35;](../ide/media/express_highlighttrue.png)

### <a name="use-intellisense-to-enter-more-code"></a>Use o IntelliSense para inserir mais código

Em seguida, use o IntelliSense para inserir mais código para abrir uma caixa de diálogo **Abrir Arquivo**. Se o usuário escolheu o botão **OK**, a PictureBox carrega o arquivo selecionado pelo usuário. As etapas a seguir mostram como inserir o código, e embora existam muitos passos, são apenas alguns toques de teclas:

 1. Comece com o texto selecionado **true** no snippet. Digite `op` para substituí-lo. (No Visual Basic, você começa com um limite inicial, portanto, digite `Op`.)

 1. A janela do **IntelliSense** é aberta e exibe **openFileDialog1**. Escolha a tecla **Tab** para selecioná-lo. (No Visual Basic, ela começa com um limite inicial, portanto, você vê **OpenFileDialog1**. Certifique-se de que **OpenFileDialog1** está selecionado.)

     Para saber mais sobre `OpenFileDialog`, consulte [OpenFileDialog](<xref:System.Windows.Forms.OpenFileDialog>).

 1. Digite um`.`período () (Muitos programadores chamam isso de ponto.) Porque você digitou um ponto logo após **abrirFileDialog1,** uma janela **do IntelliSense** é aberta, preenchida com todas as propriedades e métodos do componente **OpenFileDialog.** Estas são as mesmas propriedades exibidas na janela **Propriedades** quando você a escolhe no **Designer de Formulários do Windows**. Você também pode escolher os métodos que demandam que o componente faça coisas (como abrir uma caixa de diálogo).

    > [!NOTE]
    > A janela do **IntelliSense** pode mostrar propriedades e métodos. Para determinar o que está sendo mostrado, veja o ícone à esquerda de cada item na janela do **IntelliSense**. Você vê uma imagem de um bloco ao lado de cada método, e uma imagem de uma chave inglesa (ou chave inglesa) ao lado de cada propriedade. Há também um ícone de raio ao lado de cada evento. <br><br>Aqui estão os ícones que aparecem:<br><br>![Ícone de método](../ide/media/express_iconmethod.png)<br>![Ícone de propriedade](../ide/media/express_iconproperty.png)<br>![Ícone de evento](../ide/media/express_iconevent.png)

 1. Comece digitando `ShowDialog` (as letras maiúsculas não são importantes para o IntelliSense). O método `ShowDialog()` exibirá a caixa de diálogo **Abrir Arquivo**. Depois que a janela tiver realçado **ShowDialog**, pressione a tecla **Tab**. Você também pode realçar "ShowDialog" e escolher a tecla **F1** para obter ajuda com isso.

    Para saber mais sobre o método `ShowDialog()`, consulte [ShowDialog Method (Método ShowDialog)](<xref:System.Windows.Forms.Form.ShowDialog%2A>).

 1. Ao usar um método em um controle ou em um componente (conhecido como *chamando um método*), é necessário adicionar parênteses. Assim, insira parênteses de abertura e fechamento imediatamente após o “g” em `ShowDialog`: `()` Agora isso terá a aparência "openFileDialog1.ShowDialog()".

    > [!NOTE]
    > Os métodos são uma parte importante de qualquer aplicativo, e este tutorial mostrou várias maneiras de usar métodos. É possível chamar o método de um componente para pedir que ele faça algo, da mesma forma como você chamou o método `ShowDialog()` do componente **OpenFileDialog**. Você pode criar seus próprios métodos para fazer seu aplicativo fazer coisas, como a que você está construindo agora, chamada método, `showButton_Click()` que abre uma caixa de diálogo e uma imagem quando um usuário escolhe um botão.

 1. Para C#, adicione um espaço e adicione`==`dois sinais iguais (). Para o Visual Basic, adicione um espaço e, em seguida, use um único sinal de igual (`=`). (C# e Visual Basic usam diferentes operadores de igualdade.)

 1. Adicionar outro espaço. Assim que fizer isso, outra janela do **IntelliSense** será aberta. Comece digitando `DialogResult` e pressione a tecla **Tab** para adicioná-lo.

    > [!NOTE]
    > Quando você escreve um código para chamar um método, ele às vezes retorna um valor. Nesse caso, o método <xref:System.Windows.Forms.CommonDialog.ShowDialog> do componente **OpenFileDialog** retorna um valor <xref:System.Windows.Forms.DialogResult>. DialogResult é um valor especial que indica o que acontecem em uma caixa de diálogo. Um componente **OpenFileDialog** pode resultar em o usuário escolher **OK** ou **Cancelar**. Portanto, seu método `ShowDialog()` retorna `DialogResult.OK` ou `DialogResult.Cancel`.

 1. Digite um ponto para abrir a janela do **IntelliSense** de valor DialogResult. Insira a letra `O` e pressione a tecla **Tab** para inserir **OK**.

    Para saber mais sobre DialogResult, veja [DialogResult](<xref:System.Windows.Forms.DialogResult>).

    > [!NOTE]
    > A primeira linha de código deve ser preenchida. Para C#, deve ser semelhante ao seguinte.
    >
    >  `if (openFileDialog1.ShowDialog() == DialogResult.OK)`
    >
    >  Para o Visual Basic, deve ser o seguinte.
    >
    >  `If OpenFileDialog1.ShowDialog() = DialogResult.OK Then`

 1. Agora adicione mais uma linha de código. Você pode digitar (ou copiar e colar), mas considere usar o IntelliSense para adicioná-lo. Quanto mais familiarizado você estiver com o IntelliSense, mais rapidamente você poderá escrever seu próprio código. Seu `showButton_Click()` método final deve ser semelhante ao seguinte código.

    [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

    [!code-csharp[VbExpressTutorial1Step8#1](../ide/codesnippet/CSharp/step-8-write-code-for-the-show-a-picture-button-event-handler_1.cs)]

    [!code-vb[VbExpressTutorial1Step8#1](../ide/codesnippet/VisualBasic/step-8-write-code-for-the-show-a-picture-button-event-handler_1.vb)]

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[passo 9: Revise, comente e teste seu código](../ide/step-9-review-comment-and-test-your-code.md)**.

* Para retornar à etapa anterior do tutorial, veja [Etapa 7: Adicionar componentes de caixa de diálogo ao seu formulário](../ide/step-7-add-dialog-components-to-your-form.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
