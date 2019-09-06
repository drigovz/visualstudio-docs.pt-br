---
title: 'Etapa 7: Adicionar componentes de diálogo ao formulário'
ms.date: 08/30/2019
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
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
ms.openlocfilehash: 58721610a493283ff0bed8fca9cf6e6f6d668c4d
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293473"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Etapa 7: Adicionar componentes de diálogo ao formulário

Para habilitar seu programa a abrir arquivos de imagem e escolher uma cor da tela de fundo, nesta etapa, você adiciona um componente <xref:System.Windows.Forms.OpenFileDialog> e um componente <xref:System.Windows.Forms.ColorDialog> ao seu formulário.

Um componente é como um controle de certas maneiras. Use a **Caixa de Ferramentas** para adicionar um componente ao seu formulário e ajuste suas propriedades usando a janela **Propriedades**. Mas, diferentemente de um controle, adicionar um componente ao seu formulário não adiciona um item visível que o usuário possa ver no formulário. Em vez disso, fornece determinados comportamentos que você pode disparar com código. É um componente que abre uma caixa de diálogo **Abrir Arquivo**.

## <a name="to-add-dialog-components-to-your-form"></a>Para adicionar componentes da caixa de diálogo ao seu formulário

1. Escolha o **Designer de formulários do Windows** (**Form1.cs [Design]** ) e, em seguida, abra o grupo de **caixas de diálogo** na **caixa de ferramentas**.

    > [!NOTE]
    > O grupo **Caixas de Diálogo** na **Caixa de Ferramentas** tem componentes que abrem muitas caixas de diálogo úteis para você, que podem ser usadas para abrir e salvar arquivos, navegar por pastas e escolher fontes e cores. Você usa dois componentes de caixa de diálogo neste projeto: OpenFileDialog e ColorDialog.

1. Para adicionar um componente chamado **openFileDialog1** ao formulário, clique duas vezes em **OpenFileDialog**. Para adicionar um componente chamado **colorDialog1** ao formulário, clique duas vezes em **ColorDialog** na **Caixa de Ferramentas**. (Use a referência da próxima etapa do tutorial.) Você deve ver uma área na parte inferior da **Designer de formulários do Windows** (abaixo do formulário do **Visualizador de imagens** ) que tem um ícone para cada um dos dois componentes de caixa de diálogo que você adicionou, conforme mostrado na imagem a seguir.

     ![Componentes da caixa de diálogo](../ide/media/express_dialogsadded.png)<br>***Caixa de diálogo*** *componentes* do

1. Escolha o ícone **openFileDialog1** na área da parte inferior do **Designer de Formulários do Windows**. Defina as duas propriedades:

    - Defina a propriedade **Filtro** como o seguinte (você pode copiar e colar):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Defina a propriedade **Título** como o seguinte: **Selecionar um arquivo de imagem**

         As configurações da propriedade de **Filtro** especificam os tipos de arquivo que serão exibidos na caixa de diálogo do arquivo **Selecionar uma imagem**.

    > [!TIP]
    > Para ver um exemplo da caixa de diálogo **Abrir Arquivo** em um aplicativo diferente, abra o **Bloco de Notas** ou o **Paint** e, na barra de menus, escolha **Arquivo** > **Abrir**. Observe como há uma lista suspensa ao lado do nome do arquivo que permite escolher o tipo de arquivo. <br/><br/>Você acabou de usar a propriedade **Filter** no componente **OpenFileDialog** para configurá-la em seu aplicativo. Além disso, observe como as propriedades de **Título** e de **Filtro** estão em negrito na janela **Propriedades**. O IDE faz isso para mostrar a você todas as propriedades que tiveram seus valores padrão alterados.

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, confira [Etapa 8: Escrever o código do manipulador de eventos do botão Mostrar uma Imagem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

* Para retornar à etapa anterior do tutorial, confira [Etapa 6: Nomear os controles de botão](../ide/step-6-name-your-button-controls.md).

## <a name="see-also"></a>Consulte também

* [Tutorial 2: Criar um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Criar um jogo de correspondência](tutorial-3-create-a-matching-game.md)
