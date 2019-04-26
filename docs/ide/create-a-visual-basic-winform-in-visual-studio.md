---
title: Criar um aplicativo do Windows Forms com o Visual Basic
description: Aprenda o passo a passo de como criar um aplicativo do Windows Forms no Visual Studio com o Visual Basic.
ms.date: 03/23/2019
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang: vb
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- vb
ms.workload:
- multiple
ms.openlocfilehash: 4619a56bfe052a1fb191af8edfd1cef8b376617b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62976785"
---
# <a name="create-a-windows-forms-app-in-visual-studio-with-visual-basic"></a>Criar um aplicativo do Windows Forms no Visual Studio com o Visual Basic

Nesta introdução curta ao IDE (Ambiente de Desenvolvimento Integrado) do Visual Studio, você criará um aplicativo simples do Visual Basic que tem uma UI (interface do usuário) baseada no Windows.

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) para instalá-lo gratuitamente.

> [!NOTE]
> Algumas das capturas de tela neste tutorial usam o tema escuro. Se você não estiver usando o tema escuro, mas quiser usá-lo, confira a página [Personalizar o IDE e o Editor do Visual Studio](../ide/quickstart-personalize-the-ide.md) para saber como.

::: moniker-end

## <a name="create-a-project"></a>Criar um projeto

Primeiro, você criará um projeto de aplicativo do Visual Basic. O tipo de projeto inclui todos os arquivos de modelo que você precisará, mesmo sem adicionar nada.

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

2. Na barra de menus superior, escolha **Arquivo** > **Novo** > **Projeto**.

3. Na caixa de diálogo **Novo Projeto**, no painel esquerdo, expanda a opção **Visual Basic** e, em seguida, escolha **Área de Trabalho do Windows**. No painel central, selecione **Aplicativo do Windows Forms (.NET Framework)**. Em seguida, dê o nome `HelloWorld` para o arquivo.

     Se o modelo de projeto **Aplicativo do Windows Forms (.NET Framework)** não for exibido, cancele a caixa de diálogo **Novo Projeto** e, na barra de menus superior, escolha **Ferramentas** > **Obter Ferramentas e Recursos**. O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento de área de trabalho do .NET** e, em seguida, selecione **Modificar**.

     ![Carga de trabalho do .NET Core no Instalador do Visual Studio](../ide/media/install-dot-net-desktop-env.png)

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio 2019.

1. Na tela Iniciar, selecione **Criar um novo projeto**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na janela **Criar um novo projeto**, insira ou digite *Windows Forms* na caixa de pesquisa. Em seguida, escolha **Visual Basic** na lista Linguagem de programação e, em seguida, escolha **Windows** na lista Plataforma. 

   Depois de aplicar os filtros de linguagem de programação e de plataforma, escolha o modelo **Aplicativo do Windows Forms (.NET Framework)** e, em seguida, escolha **Avançar**.

   ![Escolher o modelo do Visual Basic para o Aplicativo do Windows Forms (.NET Framework)](../get-started/visual-basic/media/vs-2019/vb-create-new-project-search-winforms-filtered.png)

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

   ![Na janela "Configurar seu novo projeto", dê ao projeto o nome 'OláMundo'](../get-started/visual-basic/media/vs-2019/vb-name-your-winform-project-helloworld.png)

   O Visual Studio abre seu novo projeto.

::: moniker-end

## <a name="create-the-application"></a>Criar o aplicativo

Depois de selecionar o modelo de projeto do Visual Basic e nomear seu arquivo, o Visual Studio abrirá um formulário para você. Um formulário é uma interface do usuário do Windows. Vamos criar um aplicativo “Olá, Mundo” ao adicionar controles ao formulário e, então, vamos executar o aplicativo.

### <a name="add-a-button-to-the-form"></a>Adicionar um botão no formulário

1. Clique na **Caixa de Ferramentas** para abrir a janela suspensa da Caixa de Ferramentas.

     ![Clique na Caixa de Ferramentas para abrir a janela da Caixa de Ferramentas](../ide/media/vb-toolbox-toolwindow.png)

     Se você não encontrar a opção suspensa **Caixa de Ferramentas**, ela poderá ser aberta pressionando **Ctrl**+**Alt**+**X**.

2. Clique no ícone **Fixar** para encaixar a janela **Caixa de Ferramentas**.

     ![Clique no ícone Fixar para fixar a janela Caixa de Ferramentas no IDE](../ide/media/vb-pin-the-toolbox-window.png)

3. Clique no controle **Botão** e, em seguida, arraste-o para o formulário.

     ![Adicionar um botão no formulário](../ide/media/vb-add-a-button-to-form1.png)

4. Na seção **Aparência** (ou na seção **Fontes**) da janela **Propriedades**, digite `Click this`, depois pressione **Enter**.

     ![Adicionar texto no botão do formulário](../ide/media/vb-button-control-text.png)

     (Se você não encontrar a janela **Propriedades**, ela poderá ser aberta da barra de menus. Para fazer isso, clique em **Exibir** > **Janela Propriedades**. Ou pressione **F4**.)

5. Na seção **Design** da janela **Propriedades**, altere o nome de **Button1** para `btnClickThis` e, em seguida, pressione **Enter**.

     ![Adicionar uma função ao botão no formulário](../ide/media/vb-button-control-function.png)

### <a name="add-a-label-to-the-form"></a>Adicionar um rótulo ao formulário

Agora que adicionamos um controle de botão para criar uma ação, vamos adicionar um controle de rótulo para enviar o texto.

1. Selecione o controle **Rótulo** da janela **Caixa de Ferramentas** e, então, arraste-a para o formulário e solte-a abaixo do botão **Clique aqui**.

2. Na seção **Design** da janela **Propriedades**, altere o nome de **Label1** para `lblHelloWorld` e, em seguida, pressione **Enter**.

### <a name="add-code-to-the-form"></a>Adicionar código ao formulário

1. Na janela **Form1.vb &#91;Design&#93;**, clique duas vezes no botão **Clique aqui** para abrir a janela **Form1.vb**.

      (Como alternativa, você pode expandir **Form1.vb** no **Gerenciador de Soluções** e, em seguida, clicar em **Form1**.)

2. Na janela **Form1.vb**, entre a linha **Private Sub** e a linha **End Sub** (ou entre a linha **Public Class Form1** e a linha **End Class**), digite o código a seguir.

     ![Adicionar código ao formulário](../ide/media/vb-add-code-to-the-form.png)

## <a name="run-the-application"></a>Executar o aplicativo

1. Clique no botão **Iniciar** para executar o aplicativo.

     ![Clique em Iniciar para depurar e executar o aplicativo](../ide/media/vb-click-start-hello-world.png)

   Várias coisas acontecerão. No IDE do Visual Studio, a janela **Ferramentas de Diagnóstico** será aberta, e uma janela de **saída** também. Porém, fora do IDE, uma caixa de diálogo **Form1** será exibida. Ela incluirá o botão **Clique aqui** e o texto **Label1**.

2. Clique no botão **Clique aqui** na caixa de diálogo **Form1**. Observe que o texto **Label1** é alterado para **Olá, Mundo!**.

    ![Uma caixa de diálogo Form1 que inclui o texto Label1 ](../ide/media/vb-form1-dialog-hello-world.png)

Parabéns por concluir este guia de início rápido! Esperamos que você tenha aprendido um pouco sobre o Visual Basic e sobre o IDE do Visual Studio. Se quiser se aprofundar mais, continue com um tutorial na seção **Tutoriais** do sumário.

## <a name="see-also"></a>Consulte também

* [Início Rápido: Criar um aplicativo de console no Visual Studio com o Visual Basic](quickstart-visual-basic-console.md)
* [Saiba mais sobre o Visual Basic IntelliSense](visual-basic-specific-intellisense.md)
