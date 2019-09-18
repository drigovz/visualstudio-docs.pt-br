---
title: 'Etapa 11: Execute o aplicativo visualizador de imagens e tente outros recursos'
ms.date: 09/11/2019
ms.assetid: 656614d0-4fe7-4a67-8edc-c10919377d09
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
ms.openlocfilehash: 4d57852a356b2399a358f1636495e96a3dcec44f
ms.sourcegitcommit: 6993bcb0d2b0067b1b7b7899bfba52c31c70b7e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095319"
---
# <a name="step-11-run-your-picture-viewer-app-and-try-other-features"></a>Etapa 11: Execute o aplicativo visualizador de imagens e tente outros recursos

Seu aplicativo visualizador de imagens foi concluído e está pronto para ser executado. Você pode executar seu aplicativo e definir a cor do plano de <xref:System.Windows.Forms.PictureBox>fundo do. Para saber mais, tente melhorar o aplicativo alterando a cor do formulário, personalizando os botões e a caixa de seleção e alterando as propriedades do formulário.

## <a name="how-to-run-your-app-and-set-the-background-color"></a>Como executar seu aplicativo e definir a cor do plano de fundo

1. Selecione **F5** ou, na barra de menus, selecione **Depurar** > **Iniciar Depuração**.

1. Antes de abrir uma imagem, clique no botão **Definir a cor da tela de fundo**. A caixa de diálogo **Cor** é aberta.

     ![Caixa de diálogo Cor](../ide/media/express_colordialog.png)<br/>
***Cor*** do *caixa de diálogo*

1. Escolha uma cor para definir a cor do plano de fundo de PictureBox. Examine com mais detalhes `backgroundButton_Click()` o método ( `BackgroundButton_Click()`ou,) para entender como ele funciona.

    > [!NOTE]
    > Você pode carregar uma imagem da Internet colando sua URL na caixa de diálogo **Abrir Arquivo**. Tente localizar uma imagem com um plano de fundo transparente, para que sua cor do plano de fundo seja exibida.

1. Escolha o botão **Limpar a imagem** para certificar-se de que ela desaparece. Em seguida, saia do aplicativo escolhendo o botão **fechar** .

## <a name="try-other-features"></a>Experimentar outros recursos

* Altere a cor do formulário e os botões usando a propriedade **BackColor**.

* Personalize seus botões e sua caixa de seleção usando as propriedades **Font** e **ForeColor**.

* Altere as propriedades **FormBorderStyle** e **ControlBox** do formulário.

* Use as propriedades **AcceptButton** e **CancelButton** do formulário de modo que os botões sejam escolhidos automaticamente quando o usuário escolher as teclas **Enter** ou **Esc**. Faça com que o aplicativo Abra a caixa de diálogo **Abrir arquivo** quando o usuário escolher **Enter** e fechar a caixa quando o usuário escolher **ESC**.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Tutorial 2: Criar um teste de matemática cronometrado](../ide/tutorial-2-create-a-timed-math-quiz.md)

Para retornar à etapa anterior do tutorial, confira [Etapa 10: Escrever o código dos botões adicionais e de uma caixa de seleção](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

## <a name="see-also"></a>Consulte também

* [Mais C# tutoriais](/visualstudio/get-started/csharp/)
* [Mais tutoriais Visual Basic](/visualstudio/get-started/visual-basic/)
* [C++destina](/cpp/get-started/tutorial-console-cpp)
