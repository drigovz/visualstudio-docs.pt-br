---
title: 'Etapa 7: Adicionar componentes de caixa de diálogo ao formulário | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: ea98c55e-6213-4893-ba7b-f19d7f119527
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54d2b83fab24aa3c9deabc979782d9b82ea5c482
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442483"
---
# <a name="step-7-add-dialog-components-to-your-form"></a>Etapa 7: Adicionar componentes de diálogo ao formulário
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para habilitar seu programa a abrir arquivos de imagem e escolher uma cor da tela de fundo, nesta etapa, você adiciona um componente **OpenFileDialog** e um componente **ColorDialog** ao seu formulário.  
  
 Um componente é como um controle de certas maneiras. Use a Caixa de Ferramentas para adicionar um componente ao seu formulário e ajuste suas propriedades usando a janela **Propriedades**. Mas, diferentemente de um controle, adicionar um componente ao seu formulário não adiciona um item visível que o usuário possa ver no formulário. Em vez disso, fornece determinados comportamentos que você pode disparar com código. É um componente que abre uma caixa de diálogo **Abrir Arquivo**.  
  
 ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo")para uma versão em vídeo deste tópico, consulte [Tutorial 1: Criar um visualizador de imagens no Visual Basic – vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205213) ou [Tutorial 1: Criar um visualizador de imagens em c# – vídeo 3](http://go.microsoft.com/fwlink/?LinkId=205202). Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio.  
  
### <a name="to-add-dialog-components-to-your-form"></a>Para adicionar componentes da caixa de diálogo ao seu formulário  
  
1. Escolha o Designer de Formulários do Windows (Form1.cs [Design] ou Form1.vb [Design]) e abra o grupo **Caixas de Diálogo** na Caixa de Ferramentas.  
  
    > [!NOTE]
    > O grupo **Caixas de Diálogo** na Caixa de Ferramentas tem componentes que abrem muitas caixas de diálogo úteis para você, que podem ser usadas para abrir e salvar arquivos, navegar por pastas e escolher fontes e cores. Você usa dois componentes de caixa de diálogo neste projeto: **OpenFileDialog** e **ColorDialog**.  
  
2. Para adicionar um componente chamado **openFileDialog1** ao formulário, clique duas vezes em **OpenFileDialog**. Para adicionar um componente chamado **colorDialog1** ao formulário, clique duas vezes em **ColorDialog** na Caixa de Ferramentas. (Use a referência da próxima etapa do tutorial.) Você deve ver uma área na parte inferior do Windows Forms Designer (abaixo do formulário visualizador de imagens) que tem um ícone para cada um dos dois componentes da caixa de diálogo que você adicionou, conforme mostrado na seguinte imagem.  
  
     ![Componentes da caixa de diálogo](../ide/media/express-dialogsadded.png "Express_DialogsAdded")  
Componentes da caixa de diálogo  
  
3. Escolha o ícone **openFileDialog1** na área da parte inferior do Designer de Formulários do Windows. Defina as duas propriedades:  
  
    - Defina a propriedade **Filtro** como o seguinte (você pode copiar e colar):  
  
        ```  
        JPEG Files (*.jpg)|*.jpg|PNG Files (*.png)|*.png|BMP Files (*.bmp)|*.bmp|All files (*.*)|*.*  
        ```  
  
    - Defina a propriedade **Título** como o seguinte: **Selecionar um arquivo de imagem**  
  
         As configurações da propriedade de **Filtro** especificam os tipos de arquivo que serão exibidos na caixa de diálogo do arquivo **Selecionar uma imagem**.  
  
    > [!NOTE]
    > Para ver um exemplo da caixa de diálogo **Abrir Arquivo** em um aplicativo diferente, abra o Bloco de Notas ou o Paint e, na barra de menus, escolha **Arquivo**, **Abrir**. Observe como há uma lista suspensa **Arquivos de tipo** na parte inferior. Você acabou de usar a propriedade de **Filtro** no componente **OpenFileDialog** para configurar isso. Além disso, observe como as propriedades de **Título** e de **Filtro** estão em negrito na janela **Propriedades**. O IDE faz isso para mostrar a você todas as propriedades que tiveram seus valores padrão alterados.  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
- Para ir para a próxima etapa do tutorial, confira [Etapa 8: Escrever código para mostrar um manipulador de eventos do botão de imagem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).  
  
- Para retornar à etapa anterior do tutorial, confira [Etapa 6: Nomeie os controles de botão](../ide/step-6-name-your-button-controls.md).
