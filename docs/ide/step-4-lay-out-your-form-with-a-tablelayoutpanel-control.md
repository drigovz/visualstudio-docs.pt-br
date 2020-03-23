---
title: 'Etapa 4: Definir o layout do formulário com um controle TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d827077266adbe0a1ba8cabd1f19ae6d815df833
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579387"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Etapa 4: Definir o layout do formulário com um controle TableLayoutPanel

Nesta etapa, você adiciona um controle <xref:System.Windows.Forms.TableLayoutPanel> ao formulário. O TableLayoutPanel ajuda a alinhar corretamente os controles na forma que você adicionará mais tarde.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Como definir seu formulário com um controle TableLayoutPanel

1. No lado esquerdo do Visual Studio IDE, escolha a guia **Caixa de ferramentas.** (Alternativamente, escolha **Exibir** > caixa de**ferramentas** na barra de menu ou **pressione Ctrl**+**Alt**+**X**.)

1. Escolha o pequeno símbolo de triângulo ao lado do grupo **Containers** para abri-lo, conforme mostrado na captura de tela a seguir.

     ![Grupo de contêineres](../ide/media/express_toolbox.png)<br>
***Grupo de contêineres*** *group*

1. Você pode adicionar controles como botões, caixas de seleção e rótulos para seu formulário. Clique duas vezes no controle TableLayoutPanel na **caixa de ferramentas**. (Ou, você pode arrastar o controle da caixa de ferramentas para o formulário.) Quando você faz isso, o IDE adiciona um controle TableLayoutPanel à sua forma, conforme mostrado na captura de tela a seguir.

     ![Controle TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***Controle TableLayoutPanel*** *control*

    > [!NOTE]
    > Após adicionar seu TableLayoutPanel, se uma janela aparecer no formulário com o título **Tarefas de TableLayoutPanel**, clique em qualquer lugar dentro do formulário para fechá-la. Você aprenderá mais sobre esta janela mais tarde no tutorial.

     Observe como a **caixa de ferramentas** é expandida para cobrir o formulário quando você clica em sua guia e é fechada depois que você clica em qualquer lugar fora dela. Esse é o recurso Auto Hide no IDE. Você pode ligá-lo ou desatijá-lo para qualquer uma das janelas escolhendo o ícone pushpin no canto superior direito da janela para alternar Auto Hide e bloqueá-lo no lugar. O ícone de anotações aparece da seguinte maneira.

     ![Ícone de pino](../ide/media/express_pushpintoolbox.png)<br>
***Ícone pushpin*** *icon*

1. Escolha TableLayoutPanel para garantir que esteja selecionado. Você pode verificar qual controle é selecionado olhando para a lista de paradas na parte superior da janela **Propriedades,** conforme mostrado na captura de tela a seguir.

     ![Janela Propriedades mostrando o controle TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Janela propriedades*** *mostrando* *controle* ***TableLayoutPanel***

1. Escolha o botão **Alfabético** na barra de ferramentas na janela **Propriedades**. Isso classifica a lista de propriedades na janela **Propriedades** em ordem alfabética, o que facilita a localização de propriedades neste tutorial.

1. O seletor de controle é uma lista suspensa na parte superior da janela **Propriedades**. Neste exemplo, ela mostra que um controle chamado `tableLayoutPanel1` está selecionado. Você pode selecionar controles escolhendo uma área no **Designer de Formulários do Windows** ou escolhendo no seletor de controle.

   Agora que TableLayoutPanel está selecionado, localize a propriedade **Encaixar** e escolha **Encaixar**, que deve ser definida como **Nenhum**. Observe que uma seta suspensa aparece ao lado do valor. Escolha a seta e selecione o botão **'Preenchimento'** (o botão grande no meio), conforme mostrado na captura de tela a seguir.

     ![Janela Propriedades com Preenchimento selecionado](../ide/media/express_docktable.png)<br>
***Janela de propriedades*** *com* ***preenchimento*** *selecionado*

     *Encaixe* no Visual Studio refere-se a quando uma janela é anexada a outra janela ou área no IDE. Por exemplo, a janela **Propriedades** &mdash;pode ser desencaixada, ou seja, livre-flutuante dentro do Visual Studio&mdash;ou pode ser encaixada no Solution **Explorer**.

1. Depois de definir a propriedade TableLayoutPanel **Dock** para **preencher,** observe que o painel preenche todo o formulário. Se você redimensionar o formulário novamente, o TableLayoutPanel permanecerá anexado e se redimensionará para caber.

    > [!NOTE]
    > Um TableLayoutPanel funciona como uma tabela no Microsoft Office Word: tem linhas e colunas, e uma célula individual pode abranger várias linhas e colunas. Cada célula pode conter um controle (como um botão, uma caixa de seleção ou um rótulo). O TableLayoutPanel deve <xref:System.Windows.Forms.PictureBox> ter um controle que <xref:System.Windows.Forms.CheckBox> abrange toda a sua linha <xref:System.Windows.Forms.Button> superior, um controle em sua célula inferior esquerda e quatro controles em sua célula inferior direita.

1. Atualmente, o TableLayoutPanel tem duas linhas de igual tamanho e duas colunas de igual tamanho. Vamos redimensioná-los para que a linha superior e a coluna direita sejam muito maiores. No **Designer de Formulários do Windows**, selecione o TableLayoutPanel. No canto superior direito, há um pequeno botão de triângulo preto, que aparece da seguinte maneira.

     ![Botão de triângulo](../ide/media/express_iconblacktriangle.gif)<br>
***Botão triângulo*** *button*

     Este botão indica que o controle tem as tarefas que ajudam você definir suas propriedades automaticamente.

1. Escolha o triângulo para exibir a lista de tarefas do controle, conforme mostrado na captura de tela a seguir.

     ![Tarefas TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***Tarefas do TableLayoutPanel*** *tasks*

1. Escolha a tarefa **Editar Linhas e Colunas** para exibir a janela **Estilos de Coluna e Linha**. Escolha **Coluna1** e defina o tamanho como 15% certificando-se de que o botão **Porcentagem** esteja selecionado e inserindo **15** na caixa **Porcentagem**. (Isso é <xref:System.Windows.Forms.NumericUpDown> um controle, que você usará em um tutorial posterior.) Escolha **a Coluna2** e defina-a em 85%. Não escolha o botão **OK** ainda, pois a janela fechará. (Mas se você fizer isso, você pode reabri-lo usando a lista de tarefas.)

     ![Estilos de coluna e linha TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel*** *coluna e estilos de linha*

1. Na lista **de** itens de exibição na parte superior da janela Coluna e Estilos de **linha,** escolha **Linhas**. Defina **Row1** como 90% e **Row2** como 10%.

1. Clique no botão **OK**. O TableLayoutPanel agora deve ter uma grande primeira linha, uma pequena linha inferior, uma pequena coluna esquerda, e uma grande coluna direita. (Você pode redimensionar as linhas e colunas no TableLayoutPanel escolhendo **tableLayoutPanel1** no formulário e, em seguida, arrastando suas bordas de linha e coluna.)

     ![Form1 com TableLayoutPanel redimensionado](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Visualizador de imagens) com tablelayoutpanel redimensionado* ***TableLayoutPanel***

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[passo 5: Adicione controles ao seu formulário](../ide/step-5-add-controls-to-your-form.md)**.

* Para retornar à etapa anterior do tutorial, veja [Etapa 3: Definir as propriedades do formulário](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
