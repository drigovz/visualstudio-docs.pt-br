---
title: 'Etapa 5: Adicionar controles ao formulário'
ms.date: 08/30/2019
ms.assetid: dc2746f4-0b5c-4674-9ef7-f40f94150f52
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 631def96fc7e4b5d7858ea3474492b41c526da65
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579354"
---
# <a name="step-5-add-controls-to-your-form"></a>Etapa 5: Adicionar controles ao formulário

Nessa etapa, você adiciona controles como um controle <xref:System.Windows.Forms.PictureBox> e um controle <xref:System.Windows.Forms.CheckBox> em seu formulário. Para adicionar controles <xref:System.Windows.Forms.Button> ao seu formulário.

## <a name="how-to-add-controls-to-your-form"></a>Como adicionar controles à sua forma

1. Escolha a guia **Caixa de ferramentas** no lado esquerdo do Visual Studio IDE (ou pressione **Ctrl**+**Alt**+**X),** e depois expanda o grupo **Controles Comuns.** Isso mostra os controles mais comuns que você vê em formulários.

1. Clique duas vezes no item **PictureBox** para adicionar um controle PictureBox ao seu formulário. Como o TableLayoutPanel é encaixado para preencher o formulário, a IDE adiciona o controle da PictureBox à primeira célula vazia (canto superior esquerdo).

1. Escolha o novo controle **PictureBox** para selecioná-lo e escolha o triângulo preto no novo controle PictureBox para exibir sua lista de tarefas, conforme mostrado na captura de tela a seguir.

    ![Tarefas PictureBox](../ide/media/express_pictureboxtasks.png)<br/>Tarefas de *tasks* PictureBox****

    > [!NOTE]
    > Se você adicionar acidentalmente o tipo errado de controle a seu TableLayoutPanel, poderá excluí-lo. Clique com o botão direito do mouse no controle e escolha **Excluir** no menu de contexto. Você pode também remover os controles de formulário usando a barra de menus. Na barra de menu, escolha **Editar** > **desfazer**ou **Editar** > **excluir**.

1. No menu **'Tarefas de imagem'** no controle **PictureBox,** escolha o Dock no link **de contêiner pai.** Isso define automaticamente a propriedade **Dock** de PictureBox como **Fill**. Para ver isso, escolha o controle **PictureBox** para selecioná-lo, vá para a janela **Propriedades** e certifique-se de que a propriedade **Dock** está definida como **Fill**.

1. Faça a PictureBox se estender por ambas as colunas alterando sua propriedade **ColumnSpan**. Na **PictureBox,** escolha o controle **PictureBox** e defina sua propriedade **ColumnSpan** como **2**. Além disso, quando a PictureBox está vazia, você deseja mostrar uma estrutura vazia. Defina sua propriedade **BorderStyle** para **Fixed3D**.

    > [!NOTE]
    > Se você não vir uma propriedade **ColumnSpan** para sua PictureBox, então será provável que a PictureBox tenha sido adicionada ao formulário em vez de ao TableLayoutPanel. Para corrigir isso, escolha a **PictureBox**, exclua-a, escolha o **TableLayoutPanel**e adicione uma nova PictureBox.

1. Escolha o **TableLayoutPanel** no formulário e, em seguida, adicione um controle CheckBox ao formulário. Clique duas vezes no item **Caixa de seleção** na **caixa de ferramentas** para adicionar um novo controle de Caixa de Seleção à próxima célula livre em sua tabela. Como um PictureBox ocupa as duas primeiras células em TableLayoutPanel, o controle de caixa de seleção é adicionado à célula do canto inferior esquerdo. Escolha a propriedade **Texto** e digite a palavra **'Esticar',** conforme mostrado na imagem a seguir.

    ![Controle TextBox com a propriedade Stretch](../ide/media/express_pictureviewercheckbox.png)<br/>***Controle de*** *TextBox com * ***propriedade*** *Stretch*

1. Escolha o **TableLayoutPanel** no formulário e, em seguida, vá para o grupo **Containers** na **caixa de ferramentas** (onde você tem o controle TableLayoutPanel) e clique duas vezes no item **FlowLayoutPanel** para adicionar um novo controle à última célula (canto inferior direito). Em seguida, encaixe o FlowLayoutPanel no TableLayoutPanel. Você pode fazê-lo escolhendo **Dock no contêiner pai** na lista de tarefas do triângulo negro do FlowLayoutPanel ou definindo a propriedade **Dock** do FlowLayoutPanel para **preencher**.

    > [!NOTE]
    > A <xref:System.Windows.Forms.FlowLayoutPanel> é um recipiente que organiza outros controles em uma fileira, um após o outro. Quando você redimensiona um FlowLayoutPanel, ele estabelece todos os seus controles em uma única linha, se ele tiver espaço para fazê-lo. Caso contrário, organize-os em linhas, um sobre o outro. <br/><br/>Aqui, você usará um FlowLayoutPanel para segurar quatro botões. Se os botões organizarem um em cima do outro quando você adicioná-los, certifique-se de selecionar o FlowLayoutPanel antes de adicionar os botões. <br/><br/>(Normalmente, cada célula contém apenas um controle. Neste exemplo, a célula inferior direita do TableLayoutPanel contém quatro controles de botão. Por quê?  Porque o FlowLayoutPanel é um controle de contêiner, que é um controle em uma célula que contém outros controles.)

## <a name="to-add-buttons"></a>Para adicionar botões

1. Escolha o novo FlowLayoutPanel que você adicionou. Vá para **Controles Comuns** na **Caixa de Ferramentas** e clique duas vezes no item **Botão** para adicionar um controle de botão chamado **button1** ao flowlayoutPanel. Repita para adicionar outro botão. O IDE determina que já há um botão chamado **button1** e chama o próximo de **button2**.

1. Normalmente, você adiciona os outros botões usando a **caixa de ferramentas**. Desta vez, escolha **o botão2**e, em seguida, na barra de menu, escolha **Editar** > **copiar** (ou **pressione Ctrl**+**C**). Em seguida, escolha **Editar** > **colar** na barra de menu (ou **pressione Ctrl**+**V**) para colar uma cópia do botão. Agora cole-o novamente. Observe que o IDE adiciona **o botão3** e o **botão4** ao FlowLayoutPanel.

    > [!NOTE]
    > Você pode copiar e colar qualquer controle. O IDE nomeia e coloca os novos controles de uma maneira lógica. Se você colar um controle em um contêiner, o IDE escolherá o próximo espaço lógico para posicionamento.

1. Escolha o primeiro botão e defina sua propriedade **Text** como **Show a picture**. Em seguida, defina as propriedades **Text** dos próximos três botões como **Limpar a imagem**, **Definir a cor da tela de fundo** e **Fechar**.

1. Vamos dimensionar os botões e organizá-los para que eles se alinhem ao lado direito do painel. Escolha o **FlowLayoutPanel** e olhe sua propriedade **FlowDirection.** Altere-a para que ela seja definida como **RightToLeft**.

   Os botões devem alinhar-se ao lado direito da célula e inverter sua ordem para que o **botão Mostrar um** botão de imagem esteja à direita.

    > [!NOTE]
    > Se os botões ainda estiverem na ordem errada, você poderá arrastar os botões em torno do FlowLayoutPanel para reorganizá-los em qualquer ordem. Você pode escolher um botão e o arrastar para a esquerda ou direita.

1. Escolha o botão **Fechar** para selecioná-lo. Em seguida, para escolher o resto dos botões ao mesmo tempo, pressione e segure a tecla **Ctrl** e escolha-os também.

   Depois de selecionar todos os botões, vá para a janela **Propriedades** e role até a propriedade **AutoSize.** Essa propriedade informa o botão para redimensionar automaticamente para ajustar todo o texto correspondente. Defina-o **como True**.

   Os botões agora devem ser dimensionados corretamente e estar na ordem correta. (Enquanto todos os quatro botões forem selecionados, você pode alterar todas as quatro propriedades **AutoSize** ao mesmo tempo.) A imagem a seguir mostra os quatro botões.

    ![Visualizador de imagens com quatro botões](../ide/media/express_autosize.png)<br/>***Visualizador de imagens*** *com quatro botões*

1. Agora execute seu programa novamente para ver suas mudanças.

   Observe que os botões e a caixa de&mdash;seleção não fazem nada ainda, mas eles farão, em breve.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

* Para ir para a próxima etapa do tutorial, consulte **[passo 6: Nomeie os controles do botão](../ide/step-6-name-your-button-controls.md)**.

* Para retornar à etapa tutorial anterior, consulte [Passo 4: Coloque seu formulário com um controle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
