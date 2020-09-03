---
title: 'Etapa 7: adicionar componentes de diálogo ao formulário | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40b90096f768a7dd836507c83dff935261a99a25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851136"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Etapa 7: Adicionar componentes de diálogo ao formulário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para habilitar seu programa a abrir arquivos de imagem e escolher uma cor da tela de fundo, nesta etapa, você adiciona um componente **OpenFileDialog** e um componente **ColorDialog** ao seu formulário.

 Um componente é como um controle de certas maneiras. Use a Caixa de Ferramentas para adicionar um componente ao seu formulário e ajuste suas propriedades usando a janela **Propriedades**. Mas, diferentemente de um controle, adicionar um componente ao seu formulário não adiciona um item visível que o usuário possa ver no formulário. Em vez disso, fornece determinados comportamentos que você pode disparar com código. É um componente que abre uma caixa de diálogo **Abrir Arquivo**.

 ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") Para obter uma versão de vídeo deste tópico, consulte [tutorial 1: criar um visualizador de imagens no Visual Basic-video 3](https://msdn.microsoft.com/vbasic/gg315354.aspx) ou [tutorial 1: criar um visualizador de imagens em C#-vídeo 3](https://msdn.microsoft.com/vcsharp/gg278411.aspx). Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio.

### <a name="to-add-dialog-components-to-your-form"></a>Para adicionar componentes da caixa de diálogo ao seu formulário

1. Escolha o Designer de Formulários do Windows (Form1.cs [Design] ou Form1. vb [Design]) e, em seguida, abra o grupo de **caixas de diálogo** na caixa de ferramentas.

    > [!NOTE]
    > O grupo **Caixas de Diálogo** na Caixa de Ferramentas tem componentes que abrem muitas caixas de diálogo úteis para você, que podem ser usadas para abrir e salvar arquivos, navegar por pastas e escolher fontes e cores. Você usa dois componentes de caixa de diálogo neste projeto: **OpenFileDialog** e **ColorDialog**.

2. Para adicionar um componente chamado **openFileDialog1** ao formulário, clique duas vezes em **OpenFileDialog**. Para adicionar um componente chamado **colorDialog1** ao formulário, clique duas vezes em **ColorDialog** na caixa de ferramentas. (Você usará aquela na próxima etapa do tutorial.) Você deve ver uma área na parte inferior da Designer de Formulários do Windows (abaixo do formulário do Visualizador de imagens) que tem um ícone para cada um dos dois componentes de caixa de diálogo que você adicionou, conforme mostrado na imagem a seguir.

     ![Componentes da caixa de diálogo](../ide/media/express-dialogsadded.png "Express_DialogsAdded") Componentes da caixa de diálogo

3. Escolha o ícone de **OpenFileDialog1** na área na parte inferior da designer de formulários do Windows. Defina as duas propriedades:

    - Defina a propriedade **Filtro** como o seguinte (você pode copiar e colar):

        ```
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*
        ```

    - Defina a propriedade **Título** como o seguinte: **Selecionar um arquivo de imagem**

         As configurações da propriedade de **Filtro** especificam os tipos de arquivo que serão exibidos na caixa de diálogo do arquivo **Selecionar uma imagem**.

    > [!NOTE]
    > Para ver um exemplo da caixa de diálogo **Abrir Arquivo** em um aplicativo diferente, abra o Bloco de Notas ou o Paint e, na barra de menus, escolha **Arquivo**, **Abrir**. Observe como há uma lista suspensa **Arquivos de tipo** na parte inferior. Você acabou de usar a propriedade de **Filtro** no componente **OpenFileDialog** para configurar isso. Além disso, observe como as propriedades de **Título** e de **Filtro** estão em negrito na janela **Propriedades**. O IDE faz isso para mostrar a você todas as propriedades que tiveram seus valores padrão alterados.

### <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, consulte [etapa 8: escrever código para o manipulador de eventos do botão Mostrar uma imagem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

- Para retornar à etapa anterior do tutorial, consulte [etapa 6: nomear os controles de botão](../ide/step-6-name-your-button-controls.md).
