---
title: 'Criar um aplicativo UWP com o Visual Studio e o C #'
description: Criar um aplicativo UWP no Visual Studio com XAML e C#
titleSuffix: ''
ms.custom: seodec18, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 342fb2ba0d094299b41707b93b52f3b28a3afdce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909259"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Tutorial: criar seu primeiro aplicativo Plataforma Universal do Windows no Visual Studio com XAML e C&#35;

Nesta introdução ao IDE (ambiente de desenvolvimento integrado) do Visual Studio, você criará um aplicativo "Olá, Mundo" que poderá ser executado em qualquer dispositivo Windows 10. Para fazer isso, você usará um modelo de projeto da UWP (Plataforma Universal do Windows), a linguagem XAML e a linguagem de programação C#.

::: moniker range="vs-2017"
Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.
::: moniker-end
::: moniker range="vs-2019"
Se você ainda não instalou o Visual Studio, vá para a página de [downloads do Visual Studio](https://visualstudio.microsoft.com/downloads) para instalá-lo gratuitamente.
::: moniker-end

## <a name="create-a-project"></a>Criar um projeto

Primeiro, crie um projeto da Plataforma Universal do Windows. O tipo de projeto vem com todos os arquivos de modelo que você precisa, antes mesmo de você adicionar alguma coisa!

::: moniker range="vs-2017"
1. Abra o Visual Studio.

1. Na barra de menus superior, escolha **arquivo** > **novo** > **projeto**.

1. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **Visual C#** e, em seguida, escolha **Universal do Windows**. No painel do meio, escolha **Aplicativo em Branco (Universal do Windows)**. Em seguida, nomeie o projeto como *HelloWorld* e escolha **OK**.

   > [!NOTE]
   > Certifique-se de que o local do projeto de origem esteja em uma nova unidade formatada do **sistema de arquivos de tecnologia (NTFS)** , como a unidade do sistema operacional (SO). Caso contrário, você pode ter problemas para criar e executar seu projeto. 

   ![Modelo de projeto Universal do Windows na caixa de diálogo Novo Projeto no IDE do Visual Studio](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Se o modelo de projeto **Aplicativo em Branco (Universal do Windows)** não for exibido, clique no link **Abrir Instalador do Visual Studio** no painel esquerdo da caixa de diálogo **Novo Projeto**.<br><br>![Clique no link Abrir instalador do Visual Studio na caixa de diálogo Novo Projeto](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento na Plataforma Universal do Windows** e, em seguida, selecione **Modificar**.<br><br>![Carga de trabalho de desenvolvimento na Plataforma Universal do Windows no Instalador do Visual Studio](media/uwp-dev-workload.png)

1. Aceite as configurações padrão de **Versão de destino** e de **Versão mínima** na caixa de diálogo **Novo Projeto da Plataforma Universal do Windows**.

   ![Aceite as configurações padrão de Destino e de Versão mínima na caixa de diálogo Novo Projeto da Plataforma Universal do Windows](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Abra o Visual Studio e, na janela de início, selecione **Criar um novo projeto**.

1. Na janela **Criar um novo projeto**, insira *Universal Windows* na caixa de pesquisa, escolha o modelo C # para **Aplicativo em Branco (Universal Windows)** e, em seguida, escolha **Próximo**.

   ![Captura de tela de Criar um novo projeto](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Se você não vir o modelo de projeto **Aplicativo em Branco (Universal Windows)**, clique no link **Instalar mais ferramentas e recursos**.<br><br>![Clicar no link Instalar mais ferramentas e recursos](media/vs-2019/uwp-not-finding.png)<br><br>O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **Desenvolvimento na Plataforma Universal do Windows** e, em seguida, selecione **Modificar**.<br><br>![Carga de trabalho de desenvolvimento na Plataforma Universal do Windows no Instalador do Visual Studio](media/uwp-dev-workload.png)

1. Dê um nome ao projeto, _HelloWorld_, e escolha **criar**.

   ![Tela configurar seu projeto](media/vs-2019/uwp-configure-your-project.png)

1. Aceite as configurações padrão de **Versão de destino** e de **Versão mínima** na caixa de diálogo **Novo Projeto da Plataforma Universal do Windows**.

   ![Aceite as configurações de versão de destino padrão e de versão mínima na caixa de diálogo novo projeto de Plataforma Universal do Windows](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Se esta for a primeira vez que você usa o Visual Studio para criar um aplicativo UWP, uma caixa de diálogo **Configurações** poderá aparecer. Selecione **Modo do Desenvolvedor** e, em seguida, escolha **Sim**.<br><br>
   > ![Habilitar o Modo do Desenvolvedor na caixa de diálogo Configurações da UWP](media/enable-developer-mode.png)<br><br>O Visual Studio instala um pacote de Modo do Desenvolvedor adicional. Quando o pacote de instalação for concluído, feche a caixa de diálogo **Configurações**.

## <a name="create-the-application"></a>Criar o aplicativo

É hora de começar a desenvolver. Você vai adicionar um controle de botão, adicionar uma ação para o botão e, em seguida, iniciar o aplicativo "Olá, Mundo" para ver sua aparência.

### <a name="add-a-button-to-the-design-canvas"></a>Adicionar um botão à tela de Design

1. No **Gerenciador de Soluções**, clique duas vezes em *MainPage.xaml* para abrir o modo divisão.

   ::: moniker range="vs-2017"
   ![Abra o MainPage.xaml no Gerenciador de Soluções ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Abra o MainPage.xaml no Gerenciador de Soluções](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   Existem dois painéis: o **Designer XAML**, que inclui uma tela de design e o **Editor de XAML**, no qual você pode adicionar ou alterar o código.

   ![O painel Designer XAML no editor de XAML](media/uwp-xaml-editor.png)

1. Escolha **Caixa de ferramentas** para abrir a janela de submenu Caixa de Ferramentas.

   ![Clique na Caixa de Ferramentas para abrir a janela de submenu Caixa de Ferramentas](media/uwp-toolbox.png)

   (Se a opção **Caixa de Ferramentas** não for exibida, ela poderá ser aberta na barra de menus. Para fazer isso, escolha **Exibir**  >  **barra de ferramentas**. Ou pressione **Ctrl** + **ALT** + **X**.)

1. Clique no ícone **Fixar** para encaixar a janela Caixa de Ferramentas.

   ![Clique no ícone de pino para encaixar a janela Caixa de Ferramentas](media/uwp-toolbox-autohide.png)

1. Clique no controle de **Botão** e, em seguida, arraste-o para a tela de design.

   ![Clique no controle de Botão e arraste-o para a tela de Design](media/uwp-toolbox-add-button-control.png)

   Se você olhar o código no **editor XAML**, verá que o botão também foi adicionado lá:

   ![Mostrar botão no editor XAML](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Adicionar um rótulo para o botão

1. No **editor XAML**, altere o valor de conteúdo do botão de "botão" para "Olá, mundo!"

   ![Altere o valor do conteúdo do botão para Olá, Mundo](media/uwp-change-button-text-in-xaml-code-window.png)

1. Observe que o botão na **Designer XAML** também é alterado.

   ![O botão é alterado para Olá, Mundo na tela de design](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Adicionar um manipulador de eventos

O termo "Manipulador de eventos" parece complicado, mas é apenas outro nome para o código que é chamado quando ocorre um evento. Nesse caso, ele adiciona uma ação para o "Olá, Mundo!" .

1. Clique duas vezes no controle de botão na tela de design.

1. Edite o código do manipulador de eventos em *MainPage.xaml.cs*, a página code-behind.

   É aqui que as coisas ficam interessantes. O manipulador de eventos padrão tem esta aparência:

   ![O manipulador de eventos Button_Click padrão ](media/uwp-button-click-code.png)

   Vamos alterá-la para que ela tenha esta aparência:

   ![O novo manipulador de eventos Button_Click assíncrono ](media/uwp-add-hello-world-async-code.png)

   Aqui está o código a ser copiado e colado:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>O que acabamos de fazer?

O código usa algumas APIs do Windows para criar um objeto de sintetização de voz e, em seguida, fornece um texto para ele dizer. (Para obter mais informações de como usar `SpeechSynthesis`, confira <xref:System.Speech.Synthesis>.)

## <a name="run-the-application"></a>Executar o aplicativo

::: moniker range="vs-2017"
É hora de criar, implantar e iniciar o aplicativo UWP "Olá, Mundo" para ver como ele é e como ele soa. Veja como.

1. Use o botão Play (ele tem o texto **Computador Local**) para iniciar o aplicativo no computador local.

   ![Clique em um Computador Local para iniciar e depurar o aplicativo UWP](media/uwp-start-or-debug.png)

   (Como alternativa, você pode escolher **Depurar** > **Iniciar Depuração** na barra de menus ou pressionar F5 para iniciar seu aplicativo.)

1. Veja o aplicativo, que aparece logo depois que uma tela inicial desaparece. O aplicativo deve ser semelhante a este:

   ![Um aplicativo UWP "Olá, Mundo"](media/uwp-hello-world-app.png)

1. Clique no botão **Olá, Mundo**.

   Seu dispositivo Windows 10 dirá literalmente "Olá, Mundo!"

1. Para fechar o aplicativo, clique no botão **Parar Depuração** na barra de ferramentas. (Como alternativa, escolha **depurar**  >  **Pare a depuração** na barra de menus ou pressione Shift + F5.)

::: moniker-end
::: moniker range=">=vs-2019"
É hora de criar, implantar e iniciar o aplicativo UWP "Olá, Mundo" para ver como ele é e como ele soa. Veja como.

1. Use o botão Play (ele tem o texto **Computador Local**) para iniciar o aplicativo no computador local.

   ![Clique em um Computador Local para iniciar e depurar o aplicativo UWP](media/uwp-start-or-debug.png)

   (Como alternativa, você pode escolher **Depurar** > **Iniciar Depuração** na barra de menus ou pressionar F5 para iniciar seu aplicativo.)

1. Veja o aplicativo, que aparece logo depois que uma tela inicial desaparece. O aplicativo deve ser semelhante a este:

   ![Aplicativo "Olá, Mundo" UWP](media/vs-2019/uwp-hello-world-app.png)

1. Clique no botão **Olá, Mundo**.

   Seu dispositivo Windows 10 dirá literalmente "Olá, Mundo!"

1. Para fechar o aplicativo, clique no botão **Parar Depuração** na barra de ferramentas. (Como alternativa, escolha **depurar**  >  **Pare a depuração** na barra de menus ou pressione Shift + F5.)

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

Parabéns por concluir este tutorial. Esperamos que você tenha aprendido algumas noções básicas sobre a UWP e o IDE do Visual Studio. Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Criar uma interface do usuário](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Consulte também

- [Visão Geral da UWP](/windows/uwp/get-started/universal-application-platform-guide)
- [Obter exemplos de aplicativo UWP](/windows/uwp/get-started/get-uwp-app-samples)
