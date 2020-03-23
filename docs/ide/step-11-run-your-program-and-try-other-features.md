---
title: 'Passo 11: Execute seu aplicativo de visualizador de imagens e tente outros recursos'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 865064bd85d45ccb24129d289b48143321486ca1
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579894"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Passo 11: Execute seu aplicativo de visualizador de imagens e tente outros recursos

Seu aplicativo de visualizador de imagens está pronto para ser executado. Você pode executar o seu aplicativo <xref:System.Windows.Forms.PictureBox>e definir a cor de fundo do . Para saber mais, tente melhorar a aplicação alterando a cor do formulário, personalizando os botões e a caixa de seleção e alterando as propriedades do formulário.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Como executar seu aplicativo e definir a cor de fundo

1. Selecione **F5** ou, na barra de menus, selecione **Depurar** > **Iniciar Depuração**.

1. Antes de abrir uma imagem, clique no botão **Definir a cor da tela de fundo**. A caixa de diálogo **Cor** é aberta.

     ![Caixa de diálogo Cor](../ide/media/express_colordialog.png)<br/>
***Caixa de*** *diálogo de cor*

1. Escolha uma cor para definir a cor do plano de fundo de PictureBox. Olhe atentamente `backgroundButton_Click()` para `BackgroundButton_Click()`o (ou, ) método para entender como ele funciona.

    > [!NOTE]
    > Você pode carregar uma imagem da Internet colando sua URL na caixa de diálogo **Abrir Arquivo**. Tente localizar uma imagem com um plano de fundo transparente, para que sua cor do plano de fundo seja exibida.

1. Escolha o botão **Limpar a imagem** para certificar-se de que ela desaparece. Em seguida, saia do aplicativo escolhendo o botão **Fechar.**

## <a name="try-other-features"></a>Experimentar outros recursos

* Altere a cor do formulário e os botões usando a propriedade **BackColor**.

* Personalize seus botões e sua caixa de seleção usando as propriedades **Font** e **ForeColor**.

* Altere as propriedades **FormBorderStyle** e **ControlBox** do formulário.

* Use as propriedades **AcceptButton** e **CancelButton** do formulário de modo que os botões sejam escolhidos automaticamente quando o usuário escolher as teclas **Enter** ou **Esc**. Faça com que o aplicativo abra a caixa de diálogo **Arquivo Aberto** quando o usuário escolher **Entrar** e fechar a caixa quando o usuário escolher **Esc**.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Tutorial 2: Crie um teste de matemática cronometrado](../ide/tutorial-2-create-a-timed-math-quiz.md)

Para retornar à etapa anterior do tutorial, veja [Etapa 10: Escrever código para botões adicionais e uma caixa de seleção](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Confira também

* [Mais tutoriais C#](/visualstudio/get-started/csharp/)
* [Mais tutoriais do Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutorial c++](/cpp/get-started/tutorial-console-cpp)
