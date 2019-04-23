---
title: 'Etapa 11: Executar o programa e experimentar outros recursos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: de301a380eb93cd1f4dd27150f631be58f59b3eb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093898"
---
# <a name="step-11-run-your-program-and-try-other-features"></a>Etapa 11: Executar o programa e experimentar outros recursos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O programa é concluído e pronto para ser executado. Você pode executar o programa e definir a cor do plano de fundo de PictureBox. Para saber mais, tente melhorar o programa alterando a cor do formulário, personalizando os botões e a caixa de seleção, e modificando as propriedades do formulário.  
  
 Para baixar uma versão concluída do exemplo, consulte [Exemplo de tutorial completo do Visualizador de Imagens](http://code.msdn.microsoft.com/Complete-Picture-Viewer-7d91d3a8).  
  
 ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo")para uma versão em vídeo deste tópico, consulte [Tutorial 1: Criar um visualizador de imagens no Visual Basic – vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205216) ou [Tutorial 1: Criar um visualizador de imagens em c# – vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio.  
  
### <a name="to-run-your-program-and-set-the-background-color"></a>Para executar o programa e definir a cor do plano de fundo  
  
1. Selecione F5 ou, na barra de menus, selecione **Depurar**, **Iniciar Depuração**.  
  
2. Antes de abrir uma imagem, clique no botão **Definir a cor da tela de fundo**. A caixa de diálogo **Cor** é aberta.  
  
     ![Caixa de diálogo de cor](../ide/media/express-colordialog.png "Express_ColorDialog")  
Caixa de diálogo Cor  
  
3. Escolha uma cor para definir a cor do plano de fundo de PictureBox. Examine cuidadosamente o método `backgroundButton_Click()` para compreender como ele funciona.  
  
    > [!NOTE]
    >  Você pode carregar uma imagem da Internet colando sua URL na caixa de diálogo **Abrir Arquivo**. Tente localizar uma imagem com um plano de fundo transparente, para que sua cor do plano de fundo seja exibida.  
  
4. Escolha o botão **Limpar a imagem** para certificar-se de que ela desaparece. Em seguida, sai do programa escolhendo o botão **Fechar**.  
  
### <a name="to-try-other-features"></a>Para testar outros recursos  
  
- Altere a cor do formulário e os botões usando a propriedade **BackColor**.  
  
- Personalize seus botões e sua caixa de seleção usando as propriedades **Font** e **ForeColor**.  
  
- Altere as propriedades **FormBorderStyle** e **ControlBox** do formulário.  
  
- Use as propriedades **AcceptButton** e **CancelButton** do formulário de modo que os botões sejam escolhidos automaticamente quando o usuário escolher as teclas ENTER ou ESC. Faça o programa abrir a caixa de diálogo **Abrir Arquivo** quando o usuário escolher ENTER e fechar a caixa quando o usuário escolher ESC.  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
- Para aprender sobre programação no Visual Studio, consulte [Conceitos de Programação](http://msdn.microsoft.com/library/65c12cca-af4f-4017-886e-2dbc00a189d6).  
  
- Para saber mais sobre o Visual Basic, consulte [Desenvolvendo aplicativos com o Visual Basic](http://msdn.microsoft.com/library/1e1c0c81-6d95-4167-a98b-44b1efb6d25f).  
  
- Para saber mais sobre o Visual [Introdução à linguagem C# e ao .NET Framework](http://msdn.microsoft.com/library/0a2dff4e-cd84-42ff-8141-e89889b24081).  
  
- Para passar para o próximo tutorial, confira [Tutorial 2: Criar um teste de matemática temporizado](../ide/tutorial-2-create-a-timed-math-quiz.md).  
  
- Para retornar à etapa anterior do tutorial, confira [Etapa 10: Escrever código para botões adicionais e uma caixa de seleção](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).
