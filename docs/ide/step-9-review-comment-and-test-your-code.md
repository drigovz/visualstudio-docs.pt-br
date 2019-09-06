---
title: 'Etapa 9: Examinar, comentar e testar o código'
ms.date: 08/30/2019
ms.assetid: f26f79ba-c91b-4164-b87f-679a1b231c09
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
dev_langs:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6f9f5c6f3aff6338feb0de16a44d3b7d02d0c3b9
ms.sourcegitcommit: 9c07ae6fb18204ea080c8248994a683fa12e5c82
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70293642"
---
# <a name="step-9-review-comment-and-test-your-code"></a>Etapa 9: Examinar, comentar e testar o código

Em seguida, adicione um comentário ao seu código. Um comentário é uma observação que não modifica a maneira que o programa se comporta. Facilita para alguém que esteja lendo o código para entender o que ele faz. Recomendamos que você tenha o hábito de adicionar comentários ao seu código.

No C#, duas barras "//" (//) marcam uma linha como um comentário. No Visual Basic, aspas simples (') são usadas para marcar uma linha como um comentário. Após adicionar um comentário, teste seu programa. É uma prática recomendável executar e testar seu código com frequência enquanto trabalha em seus projetos e, portanto, você pode capturar e corrigir os problemas no início, antes que o código fique mais complicado. Isso é chamado de *teste iterativo*.

Você acabou de criar algo que funciona e que, embora ainda não esteja pronto, já pode carregar uma imagem. Antes de adicionar um comentário ao seu código e testá-lo, leva tempo para examinar os conceitos de código, pois você usará esses conceitos frequentemente:

- Quando você clica duas vezes no botão **Mostrar uma imagem** no **Designer de Formulários do Windows**, o IDE adiciona automaticamente um *método* ao código do seu programa.

- Métodos são o modo como você organiza seu código: É como seu código é agrupado.

- Na maioria das vezes, um método faz um pequeno número de coisas em uma ordem específica, como o `showButton_Click()` método (ou `ShowButton_Click()`) mostra uma caixa de diálogo e, em seguida, carrega uma imagem.

- Um método é composto por *declarações* de código, ou linhas de código. Pense em um método como uma maneira de empacotar as instruções de código juntas.

- Quando um método é executado, ou *chamado*, as instruções no método são excluídas em ordem, uma após a outra, começando com a primeira.

   A seguir veja um exemplo de uma declaração.

  ```csharp
  PictureBox1.Load(openFileDialog1.FileName);
  ```

  ```vb
  pictureBox1.Load(openFileDialog1.FileName)
  ```

   As instruções fazem com que seus programas funcionem. No C#, uma instrução sempre termina em um ponto e vírgula. No Visual Basic, o final de uma linha é o fim de uma declaração. (Nenhuma vírgula é necessária no Visual Basic.) A instrução anterior diz ao controle <xref:System.Windows.Forms.PictureBox> para carregar o arquivo que o usuário selecionou com o componente **OpenFileDialog**.

## <a name="to-add-comments"></a>Para adicionar comentários

1. Adicione o seguinte comentário ao seu código.

    > [!IMPORTANT]
    > Use o controle linguagem de programação no canto superior direito desta página para exibir o trecho C# de código ou o trecho de código de Visual Basic.<br><br>![Controle de linguagem de programação para Docs.Microsoft.com](../ide/media/docs-programming-language-control.png)

     [!code-csharp[VbExpressTutorial1Step9_10#1](../ide/codesnippet/CSharp/step-9-review-comment-and-test-your-code_1.cs)]
     
     [!code-vb[VbExpressTutorial1Step9_10#1](../ide/codesnippet/VisualBasic/step-9-review-comment-and-test-your-code_1.vb)]

    O manipulador de eventos do botão **showButton** <xref:System.Windows.Forms.Control.Click> foi concluído e funciona. Você começou a escrever código, começando com uma instrução `if`. Uma instrução `if` é como você dizer a seu programa, "Verifique isso, e se for verdadeiro, faça o seguinte". Nesse caso, você informa o programa para abrir a caixa de diálogo **Abrir Arquivo** e, se o usuário escolher um arquivo e o botão **OK**, carregue o arquivo na **PictureBox**.

    > [!TIP]
    > O IDE foi criado para facilitar o processo de escrever código, e os *snippets de código* são uma maneira de fazer isso. Um snippet é um atalho que é expandido em um pequeno bloco de código.
    >
    >  Você pode ver todos os snippets disponíveis. Na barra de menus, escolha **Ferramentas** > **Gerenciador de Snippets de Código**. Para C#, o `if` trecho de código está no **Visual C#**  . Para o Visual Basic, os snippets `if` estão em **Condicionais e Loops** > **Padrões de Código**. Você pode usar esse aplicativo para procurar por snippets existentes ou para adicionar seus próprios snippets.
    >
    >  Para ativar um snippet ao digitar o código, digite-o e pressione a tecla **Tab**. Muitos snippets aparecem na janela **IntelliSense** e é por isso que você escolhe a tecla **Tab** duas vezes: primeiro para marcar o snippet na janela do **IntelliSense** e, depois, para mandar o IDE para usar o snippet. (O IntelliSense oferece suporte a snippets de `if`, mas não a snippets de `ifelse`.)

1. Antes de executar o programa, salve o programa escolhendo o botão de barra de ferramentas **salvar tudo** , que deve ser semelhante à captura de tela a seguir.

     ![Botão de barra de ferramentas Salvar Todos](../ide/media/express_iconsaveall.png)<br>
***Salvar tudo*** *botão*

     Como alternativa, para salvar o programa, escolha **arquivo** > **salvar tudo** na barra de menus (ou pressione **Ctrl**+**Shift**+**S**). É uma prática recomendada salvar no início e com frequência.

     Quando estiver em execução, seu programa deverá ser semelhante à imagem a seguir.

     ![Visualizador de imagem](../ide/media/express_pictureviewerdonerun.png)<br>***Visualizador de imagem***

## <a name="to-test-your-program"></a>Para testar o programa

1. Escolha a tecla **F5** ou escolha o botão da barra de ferramentas **Iniciar Depuração**.

1. Escolha o botão **Mostrar uma imagem** para executar o código que você acabou de escrever. Primeiro, o programa abre uma caixa de diálogo **Abrir Arquivo**. Verifique se seus filtros aparecem na lista suspensa **Arquivos de tipo** na parte inferior da caixa de diálogo. Em seguida, navegue para uma imagem e abra-a. Geralmente você pode localizar as imagens de exemplo fornecidas com o sistema operacional Windows em sua pasta de *Meus Documentos*, dentro da pasta *My Pictures\Sample Pictures*.

    > [!TIP]
    > Se você não vir imagens na caixa de diálogo **Selecione um arquivo de imagem**, verifique se o filtro **Todos os arquivos (*.\*)** está marcado na lista suspensa no canto inferior direito da caixa de diálogo.

1. Carregue uma imagem e ela aparecerá em sua PictureBox. Tente redimensionar o formulário arrastando suas bordas. Como você tem seu PictureBox encaixado em um TableLayoutPanel, que está encaixado no formulário, sua área de imagem se redimensionará de modo que seja tão larga quando o formulário, e preencherá 90% da parte superior do formulário. É por isso que você usou os contêineres <xref:System.Windows.Forms.TableLayoutPanel> e <xref:System.Windows.Forms.FlowLayoutPanel>: Eles mantêm seu formato dimensionado corretamente quando o usuário o redimensiona.

     Agora, imagens maiores vão além das bordas do visualizador de imagens. Na próxima etapa, você adicionará código para fazer as imagens caberem na janela.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, confira [Etapa 10: Escrever o código dos botões adicionais e de uma caixa de seleção](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md).

- Para retornar à etapa anterior do tutorial, confira [Etapa 8: Escrever o código do manipulador de eventos do botão Mostrar uma Imagem](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md).

## <a name="see-also"></a>Consulte também

* [Tutorial 2: Criar um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Criar um jogo de correspondência](tutorial-3-create-a-matching-game.md)
