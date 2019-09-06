---
title: 'Etapa 4: Definir o layout do formulário com um controle TableLayoutPanel'
ms.date: 08/30/2019
ms.assetid: 61acde79-e115-4bad-bb06-1fbe37717a3e
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a0bc67968b7248494a087f06037f72152b53300
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293629"
---
# <a name="step-4-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Etapa 4: Definir o layout do formulário com um controle TableLayoutPanel

Nesta etapa, você adiciona um controle <xref:System.Windows.Forms.TableLayoutPanel> ao formulário. O TableLayoutPanel ajuda a alinhar corretamente os controles no formulário que você adicionará mais tarde.

## <a name="how-to-lay-out-your-form-with-a-tablelayoutpanel-control"></a>Como definir o layout do formulário com um controle TableLayoutPanel

1. No lado esquerdo do IDE do Visual Studio, escolha a guia **caixa de ferramentas** . (Como alternativa, escolha **Exibir** > **caixa de ferramentas** na barra de menus ou pressione **Ctrl**+**ALT**+**X**.)

1. Escolha o símbolo de triângulo pequeno ao lado do grupo de **contêineres** para abri-lo, conforme mostrado na captura de tela a seguir.

     ![Grupo de contêineres](../ide/media/express_toolbox.png)<br>
***Contêineres*** *grupo*

1. Você pode adicionar controles como botões, caixas de seleção e rótulos para seu formulário. Clique duas vezes no controle TableLayoutPanel na **caixa de ferramentas**. (Ou, você pode arrastar o controle da caixa de ferramentas para o formulário.) Quando você faz isso, o IDE adiciona um controle TableLayoutPanel ao formulário, conforme mostrado na captura de tela a seguir.

     ![Controle TableLayoutPanel](../ide/media/express_formtablelayout.png)<br>
***TableLayoutPanel*** *controle* do

    > [!NOTE]
    > Após adicionar seu TableLayoutPanel, se uma janela aparecer no formulário com o título **Tarefas de TableLayoutPanel**, clique em qualquer lugar dentro do formulário para fechá-la. Você aprenderá mais sobre essa janela posteriormente no tutorial.

     Observe como a **caixa de ferramentas** é expandida para cobrir o formulário quando você clica em sua guia e é fechada depois que você clica em qualquer lugar fora dela. Esse é o recurso Ocultar Automaticamente no IDE. Você pode ativar ou desativar qualquer uma das janelas escolhendo o ícone de pino no canto superior direito da janela para alternar Ocultar Automaticamente e bloqueá-lo no local. O ícone de anotações aparece da seguinte maneira.

     ![Ícone de pino](../ide/media/express_pushpintoolbox.png)<br>
***Anotação*** *ícone* do

1. Escolha TableLayoutPanel para garantir que esteja selecionado. Você pode verificar qual controle é selecionado examinando a lista suspensa na parte superior da janela **Propriedades** , conforme mostrado na captura de tela a seguir.

     ![Janela Propriedades mostrando o controle TableLayoutPanel](../ide/media/express_controlspropwin.png)<br>
***Propriedades*** do *janela mostrando* ***TableLayoutPanel*** *controle* do

1. Escolha o botão **Alfabético** na barra de ferramentas na janela **Propriedades**. Isso classifica a lista de propriedades na janela **Propriedades** em ordem alfabética, o que torna mais fácil localizar as propriedades neste tutorial.

1. O seletor de controle é uma lista suspensa na parte superior da janela **Propriedades**. Neste exemplo, ela mostra que um controle chamado `tableLayoutPanel1` está selecionado. Você pode selecionar controles escolhendo uma área no **Designer de Formulários do Windows** ou escolhendo no seletor de controle.

   Agora que TableLayoutPanel está selecionado, localize a propriedade **Encaixar** e escolha **Encaixar**, que deve ser definida como **Nenhum**. Observe que uma seta suspensa aparece ao lado do valor. Escolha a seta e, em seguida, selecione o botão **preencher** (o botão grande no meio), conforme mostrado na captura de tela a seguir.

     ![Janela Propriedades com Preenchimento selecionado](../ide/media/express_docktable.png)<br>
***Propriedades*** do *janela com* ***Preencher*** *selecionado*

     *Encaixe* no Visual Studio refere-se a quando uma janela é anexada a outra janela ou área no IDE. Por exemplo, a janela **Propriedades** pode ser desencaixada&mdash;, desanexada e sem flutuação no Visual Studio&mdash;, ou pode ser encaixada em **Gerenciador de soluções**.

1. Depois de definir a propriedade **Dock** de TableLayoutPanel como **Fill**, observe que o painel preenche todo o formulário. Se você redimensionar o formulário novamente, o TableLayoutPanel permanecerá anexado e se redimensionará para caber.

    > [!NOTE]
    > Um TableLayoutPanel funciona como uma tabela no Microsoft Office Word: Ele tem linhas e colunas e uma célula individual pode abranger várias linhas e colunas. Cada célula pode conter um controle (como um botão, uma caixa de seleção ou um rótulo). O TableLayoutPanel deve ter um <xref:System.Windows.Forms.PictureBox> controle que abranja toda a linha superior, um <xref:System.Windows.Forms.CheckBox> controle em sua célula inferior esquerda e quatro <xref:System.Windows.Forms.Button> controles em sua célula inferior direita.

1. Atualmente, o TableLayoutPanel tem duas linhas de igual tamanho e duas colunas de igual tamanho. Vamos redimensioná-las para que a linha superior e a coluna direita fiquem muito maiores. No **Designer de Formulários do Windows**, selecione o TableLayoutPanel. No canto superior direito, há um pequeno botão de triângulo preto, que aparece da seguinte maneira.

     ![Botão de triângulo](../ide/media/express_iconblacktriangle.gif)<br>
***Triângulo*** *botão*

     Este botão indica que o controle tem as tarefas que ajudam você definir suas propriedades automaticamente.

1. Escolha o triângulo para exibir a lista de tarefas do controle, conforme mostrado na captura de tela a seguir.

     ![Tarefas TableLayoutPanel](../ide/media/express_tablepanel.png)<br>
***TableLayoutPanel*** *tarefas* do

1. Escolha a tarefa **Editar Linhas e Colunas** para exibir a janela **Estilos de Coluna e Linha**. Escolha **Coluna1** e defina o tamanho como 15% certificando-se de que o botão **Porcentagem** esteja selecionado e inserindo **15** na caixa **Porcentagem**. (Esse é um <xref:System.Windows.Forms.NumericUpDown> controle, que você usará em um tutorial posterior.) Escolha **Column2** e defina-a como 85%. Não escolha o botão **OK** ainda, pois a janela fechará. (Mas, se você fizer isso, poderá reabri-lo usando a lista de tarefas.)

     ![Estilos de coluna e linha TableLayoutPanel](../ide/media/vs_tablelayoutpanel_setup.png)<br>
***TableLayoutPanel*** *estilos de coluna e linha*

1. Na lista suspensa **Mostrar** na parte superior da janela de estilos de **coluna e linha** , escolha **linhas**. Defina **Row1** como 90% e **Row2** como 10%.

1. Escolha o botão **OK**. O TableLayoutPanel agora deve ter uma grande primeira linha, uma pequena linha inferior, uma pequena coluna esquerda, e uma grande coluna direita. (Você pode redimensionar as linhas e colunas no TableLayoutPanel escolhendo **tableLayoutPanel1** no formulário e arrastando suas bordas de linha e coluna.)

     ![Form1 com TableLayoutPanel redimensionado](../ide/media/vs_formafterlayoutpanel.png)<br>
***Form1*** *(Visualizador de imagens) com redimensionado* ***TableLayoutPanel***

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, confira [Etapa 5: Adicionar controles ao formulário](../ide/step-5-add-controls-to-your-form.md).

* Para retornar à etapa anterior do tutorial, confira [Etapa 3: Definir as propriedades do formulário](../ide/step-3-set-your-form-properties.md).

## <a name="see-also"></a>Consulte também

* [Tutorial 2: Criar um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Criar um jogo de correspondência](tutorial-3-create-a-matching-game.md)
