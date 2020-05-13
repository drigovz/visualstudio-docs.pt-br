---
title: 'Crie um aplicativo do Windows Forms com C #'
description: Aprenda a criar um aplicativo do Windows Forms no Visual Studio com C#, passo a passo.
ms.date: 09/26/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8c798640ea80900c633b5b7d0817cc278a772a51
ms.sourcegitcommit: b4e0cc76d94fe8cf6d238c4cc09512d17131a195
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81224531"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-c"></a>Crie um aplicativo do Windows Forms no Visual Studio com C #

Nesta breve introdução ao ambiente de desenvolvimento integrado do Visual Studio (IDE), você criará um aplicativo C# simples que tem uma interface de usuário baseada no Windows (UI).

::: moniker range="vs-2017"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) do Visual Studio para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não instalou o Visual Studio, vá para a página [de downloads](https://visualstudio.microsoft.com/downloads) do Visual Studio para instalá-lo gratuitamente.

> [!NOTE]
> Algumas das capturas de tela neste tutorial usam o tema escuro. Se você não estiver usando o tema escuro, mas quiser usá-lo, confira a página [Personalizar o IDE e o Editor do Visual Studio](../ide/quickstart-personalize-the-ide.md) para saber como.

::: moniker-end

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo em C#. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada.

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

1. Na barra de menu superior, escolha **Arquivo** > **Novo** > **Projeto**.

1. Na caixa de diálogo **Novo Projeto** no painel esquerdo, expanda o **Visual C#** e escolha **o Windows Desktop**. No painel central, selecione **Aplicativo do Windows Forms (.NET Framework)**. Em seguida, dê o nome `HelloWorld` para o arquivo.

     Se o modelo de projeto **Aplicativo do Windows Forms (.NET Framework)** não for exibido, cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de área de trabalho do .NET** e, em seguida, selecione **Modificar**.

     ![Carga de trabalho do .NET Core no Instalador do Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio 2019.

1. Na janela inicial, escolha **Criar um novo projeto**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na **criação de uma nova** janela de projeto, escolha o modelo do Aplicativo de **formulários do Windows (.NET Framework)** para C#.

   (Se preferir, você pode refinar sua pesquisa para chegar rapidamente ao modelo que deseja. Por exemplo, digite ou digite o *Aplicativo de Formulários do Windows* na caixa de pesquisa. Em seguida, escolha **C#** na lista de idiomas e escolha **o Windows** na lista Plataforma.)  

   ![Escolha o modelo C# para o aplicativo Formulários do Windows (.NET Framework)](../get-started/csharp/media/vs-2019/csharp-create-new-winforms-project-nonfiltered.png)

   > [!NOTE]
   > Se você não encontrar o modelo do **Aplicativo do Windows Forms (.NET Framework)**, poderá instalá-lo a partir da janela **Criar um novo projeto**. Na mensagem **Não encontrou o que precisa?**, escolha o link **Instalar mais ferramentas e recursos**.
   >
   > ![O link 'Instalar mais ferramentas e recursos' da mensagem 'Não encontrou o que precisa?' na janela 'Criar novo projeto'](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Em seguida, no Instalador do Visual Studio, escolha Escolher a carga de trabalho de **desenvolvimento de área de trabalho do .NET**.
   >
   > ![Carga de trabalho do .NET Core no Instalador do Visual Studio](../ide/media/install-dot-net-desktop-env.png)
   >
   > Depois disso, escolha o botão **Modificar** no Instalador do Visual Studio. Pode ser solicitado que você salve seu trabalho; nesse caso, faça isso. Em seguida, escolha **Continuar** para instalar a carga de trabalho. Em seguida, retorne para a etapa 2 deste procedimento para "[Criar um projeto](#create-a-project)".

1. Na janela **Configurar seu novo projeto**, digite ou insira *OláMundo* na caixa **Nome do projeto**. Em seguida, escolha **Criar**.

   ![Na janela "Configurar seu novo projeto", dê ao projeto o nome 'OláMundo'](../get-started/csharp/media/vs-2019/csharp-name-your-winform-project-helloworld.png)

   O Visual Studio abre seu novo projeto.

::: moniker-end

## <a name="create-the-application"></a>Criar o aplicativo

Depois de selecionar o modelo de projeto C# e nomear seu arquivo, o Visual Studio abre um formulário para você. Um formulário é uma interface do usuário do Windows. Criaremos um aplicativo "Hello World" adicionando controles ao formulário e, em seguida, executaremos o aplicativo.

### <a name="add-a-button-to-the-form"></a>Adicionar um botão no formulário

1. Escolha **Caixa de ferramentas** para abrir a janela de submenu Caixa de Ferramentas.

     ![Escolha a caixa de ferramentas para abrir a janela Caixa de ferramentas](../ide/media/csharp-toolbox-toolwindow.png)

     (Se você não encontrar a opção suspensa **Caixa de Ferramentas**, ela poderá ser aberta da barra de menus. Para isso, **exibir** > **caixa de ferramentas**. Ou pressione **Ctrl**+**Alt**+**X**.)

1. Escolha o ícone **Pin** para acoplar a janela **Caixa de ferramentas.**

     ![Escolha o ícone Pin para fixar a janela Caixa de ferramentas no IDE](../ide/media/vb-pin-the-toolbox-window.png)

1. Escolha o **controle Button** e arraste-o para o formulário.

     ![Adicionar um botão no formulário](../ide/media/csharp-add-button-form1.png)

1. Na janela **Propriedades,** localize **Texto,** altere `Click this`o nome de **Button1** para e, em seguida, **pressione Enter**.

     ![Adicionar texto no botão do formulário](../ide/media/vb-button-control-text.png)

     (Se você não encontrar a janela **Propriedades**, ela poderá ser aberta da barra de menus. Para isso, escolha **'Exibir** > **janela propriedades'.** Ou, pressione **F4**.)

1. Na seção **Design** da janela **Propriedades**, altere o nome de **Button1** para `btnClickThis` e, em seguida, pressione **Enter**.

     ![Adicionar uma função ao botão no formulário](../ide/media/vb-button-control-function.png)

   > [!NOTE]
   > Se você tiver alfabetizado a lista na janela **Propriedades,** **Button1** aparecerá na seção **(Databindings)** em vez disso.

### <a name="add-a-label-to-the-form"></a>Adicionar um rótulo ao formulário

Agora que adicionamos um controle de botão para criar uma ação, vamos adicionar um controle de rótulo para enviar o texto.

1. Selecione o controle **Rótulo** da janela **Caixa de Ferramentas** e, então, arraste-a para o formulário e solte-a abaixo do botão **Clique aqui**.

1. Na seção **Design** ou na seção **(DataBindings)** da janela **Propriedades,** altere o nome de **Label1** para `lblHelloWorld`e, em seguida, **pressione Enter**.

### <a name="add-code-to-the-form"></a>Adicionar código ao formulário

1. Na janela **&#93;Form1.cs &#91;Design,** clique duas vezes no botão **"Clique neste** botão para abrir a janela **Form1.cs.**

      (Alternativamente, você pode expandir **Form1.cs** no **Solution Explorer**e, em seguida, escolher **Formulário1**.)

1. Na janela **Form1.cs,** após a linha de `lblHelloWorld.Text = "Hello World!";` vazio **privado,** digite ou digite conforme mostrado na captura de tela a seguir:

     ![Adicionar código ao formulário](../get-started/csharp/media/csharp-winforms-add-code.png)

## <a name="run-the-application"></a>Executar o aplicativo

1. Escolha o botão **Iniciar** para executar o aplicativo.

     ![Escolha Começar a depurar e executar o aplicativo](../ide/media/vb-click-start-hello-world.png)

   Várias coisas acontecerão. No IDE do Visual Studio, a janela **Ferramentas de Diagnóstico** será aberta, e uma janela de **saída** também. Porém, fora do IDE, uma caixa de diálogo **Form1** será exibida. Ela incluirá o botão **Clique aqui** e o texto **Label1**.

1. Escolha o **botão Clique neste** botão na caixa de diálogo **Form1.** Observe que o texto **Label1** é alterado para **Olá, Mundo!**.

    ![Uma caixa de diálogo Form1 que inclui o texto Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

1. Feche a caixa de diálogo **Form1** para parar de executar o aplicativo.

## <a name="next-steps"></a>Próximas etapas

Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Tutorial: Crie um visualizador de imagens](tutorial-1-create-a-picture-viewer.md)

## <a name="see-also"></a>Confira também

* [Mais tutoriais C#](/visualstudio/get-started/csharp/)
* [Tutoriais sobre Visual Basic](/visualstudio/get-started/visual-basic/)
* [Tutoriais c++](/cpp/get-started/tutorial-console-cpp)
