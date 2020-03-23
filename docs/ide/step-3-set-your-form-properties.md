---
title: 'Etapa 3: Definir as propriedades do formulário'
ms.date: 08/30/2019
ms.assetid: 634ef037-1525-48c8-ac7f-abf04be69376
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 82dbef4baee72be8ff96f83e436b2587e9a020ea
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579861"
---
# <a name="step-3-set-your-form-properties"></a>Etapa 3: Definir as propriedades do formulário

Em seguida, use a janela **Propriedades** para alterar a aparência do seu formulário.

## <a name="how-to-set-your-form-properties"></a>Como definir suas propriedades de formulário

1. Certifique-se de que você esteja examinando o **Designer de Formulários do Windows**. No IDE (ambiente de desenvolvimento integrado) do Visual Studio, escolha a guia **Form1.cs [Design]** (ou a guia **Form1.vb [Design]** no Visual Basic).

1. Escolha qualquer outro lugar dentro do formulário **Form1** para selecioná-lo. Examine a janela **Propriedades**, que agora deve mostrar as propriedades do formulário. Os formulários têm várias propriedades. Por exemplo, você pode definir a cor de primeiro plano e do plano de fundo, o texto do título que aparece na parte superior do formulário, o tamanho do formulário e outras propriedades.

   > [!NOTE]
   > Se a janela **Propriedades** não aparecer, pare seu aplicativo escolhendo o botão quadrado **Stop Debugging** na barra de ferramentas ou apenas feche a janela. Se o aplicativo estiver parado e você ainda não ver a janela **Propriedades,** na barra de menu, escolha **'Exibir** > **janelas propriedades ''**

1. Depois que o formulário for selecionado, localize a propriedade de **Texto** na janela **Propriedades**. Dependendo de como a lista estiver classificada, talvez seja necessário rolar para baixo. Escolha **Texto**, digite **Visualizador de Imagens** e escolha **Enter**.  Seu formulário agora deve ter o visualizador **de imagem** de texto em sua barra de título, e a janela **Propriedades** deve ser semelhante à captura de tela a seguir.

    ![Janela Propriedades](../ide/media/express_edittextproperty.png)<br>
   ***Janela de propriedades*** *window*

   > [!NOTE]
   > As propriedades podem ser classificadas por um modo **Categorizado** ou **Alfabético**. É possível mude entre essas duas modos de exibição usando os botões na janela **Propriedades**. Neste tutorial, é mais fácil localizar propriedades por meio da exibição **Alfabética**.

1. Volte ao **Designer de Formulários do Windows**. Escolha a alça inferior direita do formulário, que é o pequeno quadrado branco no canto inferior direito do formulário e aparece da seguinte maneira.

    ![Arraste a alça](../ide/media/express_bottomrt_drag.png)<br>
   *Alça de arrasto*

    Arraste a alça para redimensionar o formulário para que o formulário fique mais amplo e um pouco mais alto.

1. Examine a janela **Propriedades** e observe que a propriedade **Tamanho** foi alterada. A propriedade **Tamanho** é alterada a cada vez que você redimensiona o formulário. Tente arrastar a alça do formulário para redimensioná-la para um tamanho de aproximadamente **550, 350** (não é preciso ser exato), o que deve funcionar bem para este projeto. Como alternativa, é possível inserir os valores diretamente na propriedade **Tamanho** e, em seguida, pressionar a tecla **Enter**.

1. Execute seu aplicativo novamente. Lembre-se, você pode usar qualquer um dos seguintes métodos para executar o seu aplicativo.

   - Pressione a tecla **F5**.

   - Na barra de menu, escolha **Depurar** > **depuração**.

   - Na barra de ferramentas, clique no botão **Iniciar Depuração**, que aparece da seguinte maneira.

      ![Botão de barra de ferramentas Iniciar Depuração](../ide/media/express_icondebug.png)<br>
     Iniciar botão de barra de *ferramentas* ***de depuração***

     Assim como antes, o IDE constrói e executa seu aplicativo, e uma janela aparece.

1. Antes de ir para o próximo passo, pare seu aplicativo, porque o IDE não permite que você altere seu aplicativo enquanto ele estiver em execução. Lembre-se, você pode usar qualquer um dos seguintes métodos para parar o seu aplicativo.

   - Na barra de ferramentas, clique no botão **Parar Depuração**.

   - Na barra de menu, escolha **Depurar** > **Parar de Depurar**.

   - Use o teclado e **pressione Shift**+**F5**.

   - Escolha o botão **X** no canto superior da janela **Visualizador de imagens.**

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[passo 4: Coloque seu formulário com um controle TableLayoutPanel](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)**.

* Para retornar à etapa tutorial anterior, consulte [Passo 2: Execute seu aplicativo de visualização de imagens](../ide/step-2-run-your-program.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
