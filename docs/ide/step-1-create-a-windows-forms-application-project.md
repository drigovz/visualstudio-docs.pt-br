---
title: 'Passo 1: Crie um projeto de aplicativo do Windows Forms'
ms.date: 08/30/2019
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d5e34d825d2a4d296a8a394105b412195b4e3fb
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579907"
---
# <a name="step-1-create-a-windows-forms-app-project"></a>Passo 1: Crie um projeto de aplicativo do Windows Forms

Quando você cria um visualizador de imagens, o primeiro passo é criar um projeto do Aplicativo De Formulários do Windows.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Abra o Visual Studio 2017

1. Na barra de menu, escolha **Arquivo** > **Novo** > **Projeto**. A caixa de diálogo deve ser semelhante à captura de tela a seguir.

     ![Caixa de diálogo Novo Projeto](../ide/media/newprojectdialogcallouts.png)<br/>***Caixa de diálogo*** *Novo Projeto*

2. No lado esquerdo da caixa de diálogo **Novo Projeto,** escolha **visual C#** ou **Visual Basic**e escolha **Windows Desktop**.

3. Na lista de modelos de projeto, escolha **o Aplicativo Formulários do Windows (.NET Framework)**. Dê o nome de *PictureViewer* ao novo formulário e escolha o botão **OK**.

    >[!NOTE]
    >Se o modelo **Aplicativo do Windows Forms (.NET Framework)** não for exibido, use o Instalador do Visual Studio para instalar a carga de trabalho **Desenvolvimento para área de trabalho do .NET**.<br/><br/>![Carga de trabalho de desenvolvimento para carga de trabalho do .NET no Instalador do Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Para obter mais informações, confira a página [Instalar o Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Abrir o Visual Studio 2019

1. Na janela inicial, escolha **Criar um novo projeto**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na janela **Criar um novo projeto**, insira ou digite *Windows Forms* na caixa de pesquisa. Em seguida, escolha **Desktop** na lista **de tipos de projeto.**

   Depois de aplicar o filtro **tipo Projeto,** escolha o modelo **do Aplicativo de formulários do Windows (.NET Framework)** para C# ou Visual Basic e escolha **Next**.

   ![Escolha o modelo C# ou Visual Basic para o Aplicativo Formulários do Windows (.NET Framework)](./media/create-new-project-search-winforms-filtered.png)

   > [!NOTE]
   > Se você não ver o modelo **do Aplicativo de formulários do Windows (.NET Framework),** poderá instalá-lo a partir da nova janela **criar um novo projeto.** Na mensagem **Não encontrou o que precisa?**, escolha o link **Instalar mais ferramentas e recursos**.
   >
   > ![O link 'Instalar mais ferramentas e recursos' da mensagem 'Não encontrou o que precisa?' na janela 'Criar novo projeto'](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Em seguida, no Instalador do Visual Studio, escolha Escolher a carga de trabalho de **desenvolvimento de área de trabalho do .NET**.
   >
   > ![Carga de trabalho do .NET Core no Instalador do Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Depois disso, escolha o botão **Modificar** no Instalador do Visual Studio. Pode ser solicitado que você salve seu trabalho; nesse caso, faça isso. Em seguida, escolha **Continuar** para instalar a carga de trabalho.

1. Na janela **Configurar seu novo projeto**, digite ou insira *PictureViewer* na caixa **Nome do projeto**. Em seguida, escolha **Criar**.

::: moniker-end

O Visual Studio cria uma solução para o seu aplicativo. Uma solução funciona como um contêiner para todos os projetos e arquivos necessários pelo seu aplicativo. Esses termos serão explicados em mais detalhes posteriormente neste tutorial.

## <a name="about-the-windows-forms-app-project"></a>Sobre o projeto do Aplicativo Formulários do Windows

1. O ambiente de desenvolvimento contém três janelas: uma janela principal, o **Gerenciador de Soluções** e a janela **Propriedades**.

     Se alguma dessas janelas estiver faltando, você pode restaurar o layout padrão da janela. Na barra de menus, escolha > **''Redefinir a janela' Layout da janela**. **Window**

     Você também pode exibir janelas usando os comandos de menu. Na barra de menus, escolha **Exibir** > **janela de propriedades** ou explorador de **soluções**.

     Se qualquer outra janela está aberta, feche-a escolhendo o botão **Fechar** (x) no canto superior direito.

    ::: moniker range="vs-2017"

    * **Janela principal** Nesta janela você fará a maior parte de seu trabalho, como trabalhar com formulários e editar códigos. A janela mostra um formulário no **Editor de Formulários**. Na parte superior da janela, a guia **Página Inicial** e a guia **Form1.cs [Design]** aparecem. (No Visual Basic, o nome da guia termina com *.vb* em vez de *.cs*.)

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    * **Janela principal** Nesta janela você fará a maior parte de seu trabalho, como trabalhar com formulários e editar códigos. A janela mostra um formulário no **Editor de Formulários**.

    ::: moniker-end

    * **Janela do Solution Explorer** Nesta janela, você pode visualizar e navegar para todos os itens da sua solução.

    Se você escolher um arquivo, o conteúdo da janela **Propriedades** será alterado. Se você abrir um arquivo de código (que termina em *.cs* em C# e *.vb* no Visual Basic), o arquivo de código ou um designer para o arquivo de código será exibido. Um designer é uma superfície visual na qual você pode adicionar controles, como botões e listas. Para formulários do Visual Studio, o designer é chamado no **Designer de Formulários do Windows**.

    * **Janela de propriedades** Nesta janela, você pode alterar as propriedades dos itens que você escolhe nas outras janelas. Por exemplo, se você escolher o Form1, você poderá alterar o título configurando a propriedade **Text** e você poderá alterar a cor da tela de fundo configurando a propriedade **Backcolor**.

      > [!NOTE]
      > A linha superior no **Gerenciador de Soluções** mostra **Solução "PictureViewer" (1 projeto)**, o que significa que o Visual Studio criou uma solução para você. Uma solução pode conter mais de um projeto, mas por enquanto, você trabalhará com soluções que contêm somente um projeto.

1. Na barra de menu, escolha **'Salvar todos'** **do arquivo** > .

     Como alternativa, escolha o botão **Salvar tudo** na barra de ferramentas, que a imagem a seguir mostra.

     ![Botão de barra de ferramentas Salvar Todos](../ide/media/express_iconsaveall.png)<br/>
     ***Salvar todos os*** *botões da barra de ferramentas*

     O Visual Studio preenche automaticamente o nome da pasta e o nome do projeto e, em seguida, salva o projeto na sua pasta de projeto.

## <a name="next-steps"></a>Próximas etapas

* Para ir para a próxima etapa do tutorial, consulte **[Passo 2: Execute seu aplicativo](../ide/step-2-run-your-program.md)**.

* Para retornar ao tópico visão geral, consulte [Tutorial 1: Crie um visualizador de imagens](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Confira também

* [Tutorial 2: Crie um teste de matemática cronometrado](tutorial-2-create-a-timed-math-quiz.md)
* [Tutorial 3: Crie um jogo de correspondência](tutorial-3-create-a-matching-game.md)
