---
title: 'Etapa 1: Criar um projeto de aplicativo do Windows Forms'
ms.date: 03/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 16ac2422-e720-4e3a-b511-bc2a54201a86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f529d737816406b3a4f6aa9921a8dc6b902d2fb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979844"
---
# <a name="step-1-create-a-windows-forms-application-project"></a>Etapa 1: Criar um projeto de aplicativo do Windows Forms

Ao criar um visualizador de imagens, a primeira etapa é criar um projeto de aplicativo do Windows Forms.

 > [!TIP]
 > ![link para vídeo](../data-tools/media/playvideo.gif) Para obter uma versão em vídeo deste tópico, confira [Tutorial 1: Criar um visualizador de imagens em Visual Basic – Vídeo 1](http://go.microsoft.com/fwlink/?LinkId=205209) ou [Tutorial 1: Criar um visualizador de imagens em C# – Vídeo 1](http://go.microsoft.com/fwlink/?LinkId=205199). Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio.

::: moniker range="vs-2017"

## <a name="open-visual-studio-2017"></a>Abra o Visual Studio 2017

1. Na barra de menus, selecione **Arquivo** > **Novo** > **Projeto**. A caixa de diálogo deve ser assim.

     ![Caixa de diálogo Novo Projeto](../ide/media/newprojectdialogcallouts.png)<br/>
*Caixa de diálogo **Novo projeto***

2. Escolha **Visual C#** ou **Visual Basic** no lado esquerdo da caixa de diálogo **Novo Projeto**.

3. Na lista de modelos, escolha **Aplicativo do Windows Forms (.NET Framework)**. Dê o nome de **PictureViewer** ao novo formulário e escolha o botão **OK**.

    >[!NOTE]
    >Se o modelo **Aplicativo do Windows Forms (.NET Framework)** não for exibido, use o Instalador do Visual Studio para instalar a carga de trabalho **Desenvolvimento para área de trabalho do .NET**.<br/><br/>![Carga de trabalho de desenvolvimento para carga de trabalho do .NET no Instalador do Visual Studio](../ide/media/dot-net-desktop-dev-workload.png)<br/><br/> Para obter mais informações, confira a página [Instalar o Visual Studio](../install/install-visual-studio.md).

::: moniker-end

::: moniker range="vs-2019"

## <a name="open-visual-studio-2019"></a>Abrir o Visual Studio 2019

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
   > Depois disso, escolha o botão **Modificar** no Instalador do Visual Studio. Pode ser solicitado que você salve seu trabalho; nesse caso, faça isso. Em seguida, escolha **Continuar** para instalar a carga de trabalho. 

1. Na janela **Configurar seu novo projeto**, digite ou insira *PictureViewer* na caixa **Nome do projeto**. Em seguida, escolha **Criar**.

::: moniker-end

O Visual Studio cria uma solução para seu programa. Uma solução atua como um recipiente para todos os projetos e arquivos necessários pelo seu programa. Esses termos serão explicados em mais detalhes posteriormente neste tutorial.

## <a name="about-the-windows-forms-application-project"></a>Sobre o projeto para o aplicativo do Windows Forms

1. O ambiente de desenvolvimento contém três janelas: uma janela principal, o **Gerenciador de Soluções** e a janela **Propriedades**.

     Se qualquer uma das janelas estiver faltando, restaure o layout de janela padrão ao escolher, na barra de menus, **Janela** > **Redefinir Layout da Janela**. Você também pode exibir janelas usando os comandos de menu. Na barra de menus, escolha **Modo de Exibição** > **Janela Propriedades** ou **Gerenciador de Soluções**. Se qualquer outra janela está aberta, feche-a escolhendo o botão **Fechar** (x) no canto superior direito.

    ::: moniker range="vs-2017"

    - **Janela principal** Nesta janela você fará a maior parte de seu trabalho, como trabalhar com formulários e editar códigos. A janela mostra um formulário no **Editor de Formulários**. Na parte superior da janela, a guia **Página Inicial** e a guia **Form1.cs [Design]** aparecem. (No Visual Basic, o nome da guia termina com *.vb*, em vez de *.cs*).

    ::: moniker-end

    ::: moniker range=">=vs-2019"

    - **Janela principal** Nesta janela você fará a maior parte de seu trabalho, como trabalhar com formulários e editar códigos. A janela mostra um formulário no **Editor de Formulários**.

    ::: moniker-end

    - **Janela do Gerenciador de Soluções** Nesta janela, você pode exibir e navegar em todos os itens na solução. Se você escolher um arquivo, o conteúdo da janela **Propriedades** será alterado. Se você abrir um arquivo de código (que termine com *.cs* no Visual C# e com *.vb* no Visual Basic), o arquivo de código ou um designer para o arquivo de código será exibido. Um designer é uma superfície visual na qual você pode adicionar controles, como botões e listas. Para formulários do Visual Studio, o designer é chamado no **Designer de Formulários do Windows**.

    - **Janela Propriedades** Nessa janela, você pode alterar as propriedades dos itens escolhidos nas outras janelas. Por exemplo, se você escolher o Form1, você poderá alterar o título configurando a propriedade **Text** e você poderá alterar a cor da tela de fundo configurando a propriedade **Backcolor**.

    > [!NOTE]
    > A linha superior no **Gerenciador de Soluções** mostra **Solução "PictureViewer" (1 projeto)**, o que significa que o Visual Studio criou uma solução para você. Uma solução pode conter mais de um projeto, mas por enquanto, você trabalhará com soluções que contêm somente um projeto.

1. Na barra de menus, escolha **Arquivo** > **Salvar Todos**.

     Como alternativa, escolha o botão **Salvar Todos** na barra de ferramentas, demostrado na ilustração a seguir.

     ![Botão de barra de ferramentas Salvar Todos](../ide/media/express_iconsaveall.png)<br/>
     *Botão de barra de ferramentas **Salvar tudo***

     O Visual Studio preenche automaticamente o nome da pasta e o nome do projeto e, em seguida, salva o projeto na sua pasta de projeto.

## <a name="to-continue-or-review"></a>Para continuar ou revisar

- Para ir para a próxima etapa do tutorial, confira [Etapa 2: Executar o programa](../ide/step-2-run-your-program.md).

- Para retornar ao tópico de visão geral, confira [Tutorial 1: Criar um visualizador de imagens](../ide/tutorial-1-create-a-picture-viewer.md).

## <a name="see-also"></a>Consulte também

- [Criando um formulário do Windows](/dotnet/framework/winforms/creating-a-new-windows-form/)