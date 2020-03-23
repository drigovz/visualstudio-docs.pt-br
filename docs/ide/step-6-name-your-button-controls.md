---
title: 'Etapa 6: Nomear os controles de botão'
ms.date: 08/30/2016
ms.assetid: 56b3baa3-651e-4ad4-8942-e334c5c57158
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
ms.openlocfilehash: a5c23f48e803665e00155d1b546ace4e4ec7bc54
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579798"
---
# <a name="step-6-name-your-button-controls"></a>Etapa 6: Nomear os controles de botão

Há apenas uma <xref:System.Windows.Forms.PictureBox> em seu formulário. Quando você a adicionou, o IDE a nomeou automaticamente como **pictureBox1**. Há apenas uma <xref:System.Windows.Forms.CheckBox>, que é denominada **checkBox1**. Em breve, você escreverá algum código, e esse código se referirá à Caixa de Seleção e à Caixa de Imagens. Como há apenas um desses controles, você saberá o que significa quando você ver **pictureBox1** ou **checkBox1** em seu código.

> [!TIP]
> No Visual Basic, a primeira letra padrão de qualquer nome de controle é uma maiúscula inicial e, portanto, os nomes são **PictureBox1**, **CheckBox1** e assim por diante.

Há quatro botões no formulário e o IDE os nomeou **button1**, **button2**, **button3** e **button4**. Apenas olhando seus nomes atuais, você não consegue saber qual botão é o botão de **Fechar** e qual é o botão **Mostrar uma imagem**. É por isso que é útil atribuir nomes mais informativos aos controles de botão.

## <a name="to-name-your-button-controls"></a>Para nomear os controles de botão

1. No formulário, clique no botão **Fechar**. (Se você ainda tiver todos os botões selecionados, escolha a chave **Esc** para cancelar a seleção.) Role na janela **Propriedades** até ver a propriedade **(Nome).** (A propriedade **(Nome)** está perto do topo quando as propriedades são alfabéticas.) Altere o nome para **fecharButton,** como mostrado na captura de tela a seguir.

    ![A janela Propriedades com nome de closeButton](../ide/media/express_setnameproperty.png)<br>***Janela de propriedades*** *com* nome ***de botão fechado*** *name*

    > [!NOTE]
    > Tente alterar o nome do botão para **fechar button**, com um espaço entre as palavras "fechar" e "Botão". Quando você faz isso, o IDE exibe uma mensagem de erro: "O valor da propriedade não é válido". Espaços (e mais alguns caracteres) não são permitidos em nomes de controle.

1. Renomeie os outros três botões para **backgroundButton**, **clearButton** e **showButton**.
Você pode verificar os nomes escolhendo a lista suspensa seletora de controle na janela **Propriedades**. Os nomes dos novos botões aparecem.

1. Clique duas vezes no botão **Mostrar uma imagem** no formulário. Como alternativa, escolha o **Botão Mostrar um** botão de imagem no formulário e, em seguida, pressione a tecla **Enter.** Quando o fizer, o IDE abre uma guia adicional na janela principal chamada **Form1.cs**. (Se você estiver usando o Visual Basic, a guia é chamada **Form1.vb**).

   Esta guia exibe o arquivo de código atrás do formulário, como mostrado na captura de tela a seguir.

    ![Guia Form1.cs com código do Visual C&#35;](../ide/media/express_showbuttoncode.png)<br>
***Form1.cs*** *guia com código C#*

    > [!NOTE]
    > A guia Form1.cs ou Form1.vb pode exibir **showButton** como **ShowButton.**

1. Foco nesta parte do código.

    ```csharp
        private void ShowButton_Click(object sender, EventArgs e)
    {
    }
    ```

    ```vb
        Private Sub showButton_Click() Handles showButton.Click

    End Sub
    ```

   [!INCLUDE [devlang-control-csharp-vb](./includes/devlang-control-csharp-vb.md)]

   Você está olhando `showButton_Click()` para o `ShowButton_Click()`código chamado (alternativamente, ). O IDE adicionou isto ao código do formulário quando você abriu o arquivo de código para o botão **showButton**. No tempo de design, quando você abre o arquivo de código para um controle em um formulário, o código é gerado para o controle se ainda não existir. Este código, conhecido como *método,* é executado quando você executa seu aplicativo e escolhe o controle - neste caso, o **Botão Mostrar uma imagem.**

1. Escolha novamente a guia **Windows Forms Designer** **(Form1.cs [Design]**) e, em seguida, abra o arquivo de código para o botão **Limpar a imagem** para criar um método para ele no código do formulário. Repita isso para os dois botões restantes. A cada vez, o IDE adiciona um novo método ao arquivo de código do formulário.

1. Para adicionar mais um método, abra o arquivo de código para o controle `checkBox1_CheckedChanged()` **CheckBox** no Windows Forms **Designer** para fazer o IDE adicionar um método. Esse método é chamado sempre que o usuário seleciona ou desmarca a caixa de seleção.

   > [!TIP]
   > Ao trabalhar em um aplicativo, muitas vezes você se move entre o editor de código e o **Windows Forms Designer**. O IDE torna fácil a navegação no projeto. Use **o Solution Explorer** para abrir o Windows Forms **Designer** clicando duas vezes em *Form1.cs* em C# ou *Form1.vb* no Visual Basic, ou na barra de menu, escolha **Exibir** > **Designer**.

    A seguir temos o novo código que você vê no editor de códigos.

    [!code-csharp[VbExpressTutorial1Step6_#2](../ide/codesnippet/CSharp/step-6-name-your-button-controls_2.cs)]

    [!code-vb[VbExpressTutorial1Step6_#2](../ide/codesnippet/VisualBasic/step-6-name-your-button-controls_2.vb)]

    > [!NOTE]
    > Seu código pode não exibir manipuladores de eventos em letras "camelCase".

    Os cinco métodos adicionados são chamados *manipuladores de eventos,* porque seu aplicativo os chama sempre que um evento (como um usuário escolhendo um botão ou selecionando uma caixa) acontece.

    Ao exibir o código para um controle no IDE em tempo de design, o Visual Studio adiciona um método manipulador de eventos para o controle se um não estiver presente. Por exemplo, quando você clica duas vezes em um botão, o IDE adiciona um manipulador de eventos para seu evento <xref:System.Windows.Forms.Control.Click> (que é chamado sempre que o usuário escolhe o botão). Quando você clica duas vezes em uma caixa de seleção, o IDE adiciona um manipulador de eventos para o evento <xref:System.Windows.Forms.CheckBox.CheckedChanged> (que é chamado sempre que o usuário seleciona ou desmarca a caixa).

    Após adicionar um manipulador de eventos para um controle, você pode retornar a ele a qualquer momento do **Designer de Formulários do Windows** clicando duas vezes no controle ou na barra de menus, selecionando **Exibir** > **Código**.

    Os nomes são importantes quando você cria programas e métodos (incluindo manipuladores de eventos) podem ter qualquer nome que você desejar. Quando você adiciona um manipulador de eventos com o IDE, cria um nome com base no nome do controle e do evento que está sendo tratado.

    Por exemplo, o evento Click para um `showButton_Click()` botão chamado `ShowButton_Click()` **showButton** é chamado de método (alternativamente), de manipulador de eventos. Além disso, os parênteses de abertura e fechamento `()` são adicionados geralmente após o nome do método para indicar que os métodos estão sendo discutidos.

    Se você decidir alterar um nome de variável de código, clique com o botão direito do mouse na variável no código e, em seguida, escolha > **Renomerefactor**. **Refactor** Todas as instâncias desta variável no código são renomeadas. Para obter mais informações, consulte [Refatoração de renomeação](../ide/reference/rename.md).

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[Passo 7: Adicione componentes de diálogo ao seu formulário](../ide/step-7-add-dialog-components-to-your-form.md)**.

* Para retornar à etapa tutorial anterior, consulte [Passo 5: Adicione controles ao seu formulário](../ide/step-5-add-controls-to-your-form.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
