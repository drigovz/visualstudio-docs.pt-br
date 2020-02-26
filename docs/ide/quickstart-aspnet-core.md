---
title: Criar um aplicativo Web ASP.NET Core em C#
description: Saiba como criar um aplicativo Web simples do Olá, Mundo no Visual Studio com C# e ASP.NET Core, passo a passo.
ms.custom: mvc,seodec18
ms.date: 11/06/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: quickstart
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 1873c11d8f2e6243a0dc0f867e579f1927cd1607
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579968"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Início rápido: Usar o Visual Studio para criar seu primeiro aplicativo Web ASP.NET Core

Nesta introdução de 5 a 10 minutos que mostra como usar o Visual Studio, você criará um aplicativo Web "Olá, Mundo" simples usando um modelo de projeto ASP.NET e a linguagem de programação C#.

## <a name="before-you-begin"></a>Antes de começar

### <a name="install-visual-studio"></a>Instalar Visual Studio

::: moniker range="vs-2017"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) para instalá-lo gratuitamente.

::: moniker-end

::: moniker range="vs-2019"

Se você ainda não tiver instalado o Visual Studio, acesse a página [Downloads do Visual Studio](https://visualstudio.microsoft.com/downloads) para instalá-lo gratuitamente.

::: moniker-end

### <a name="choose-your-theme-optional"></a>Escolher o tema (opcional)

Este tutorial de início rápido inclui capturas de tela que usam o tema escuro. Se você não estiver usando o tema escuro, mas quiser usá-lo, confira a página [Personalizar o IDE e o Editor do Visual Studio](quickstart-personalize-the-ide.md) para saber como.

## <a name="create-a-project"></a>Criar um projeto

Para começar, você criará um projeto de aplicativo Web ASP.NET Core. O tipo de projeto vem com todos os arquivos de modelo para criar um aplicativo Web, antes mesmo de você adicionar alguma coisa!

::: moniker range="vs-2017"

1. Abra o Visual Studio 2017.

1. Na barra de menus superior, escolha **arquivo** > **novo** **projeto**de >.

1. No painel esquerdo da caixa de diálogo **Novo Projeto**, expanda **Visual C#** e, em seguida, escolha **.NET Core**. No painel central, escolha **Aplicativo Web ASP.NET Core**. <br/><br/>Em seguida, nomeie o arquivo `HelloWorld` e escolha **OK**.

   ![Crie o novo projeto de aplicativo Web ASP.NET Core para C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Se você não vir a categoria de modelo de projeto **.NET Core**, escolha o link **Abrir Instalador do Visual Studio** no painel esquerdo. (Dependendo das suas configurações de exibição, talvez seja necessário rolar para vê-la.)
   >
   > ![Abrir Instalador do Visual Studio na caixa de diálogo Novo Projeto](../ide/media/open-visual-studio-installer.png)
   >
   > O Instalador do Visual Studio é iniciado. Escolha a carga de trabalho **ASP.NET e desenvolvimento para a Web** e, em seguida, selecione **Modificar**.
   >
   > ![Carga de trabalho ASP.NET no instalador do VS](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Talvez você precise fechar o Visual Studio antes de continuar a instalar a nova carga de trabalho.)

1. Na caixa de diálogo **Novo aplicativo Web ASP.NET Core**, selecione **ASP.NET Core 2.1** no menu suspenso superior. Em seguida, escolha **Aplicativo Web** e, em seguida, **OK**.

   ![Caixa de diálogo Novo Aplicativo Web ASP.NET Core](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Se o **ASP.NET Core 2.1** não for exibido, verifique se você está executando a versão mais recente do Visual Studio. Para obter mais informações de como atualizar sua instalação, confira a página [Atualizar o Visual Studio para a versão mais recente](../install/update-visual-studio.md).

Logo depois, o Visual Studio abre o arquivo de projeto.

::: moniker-end

::: moniker range="vs-2019"

1. Abra o Visual Studio.

1. Na tela Iniciar, selecione **Criar um novo projeto**.

   ![Exibir a janela 'Criar um novo projeto'](../get-started/media/vs-2019/create-new-project-dark-theme.png)

1. Na janela **Criar um novo projeto**, insira ou digite *ASP.NET* na caixa de pesquisa. Em seguida, escolha **C#** na lista Linguagem de programação e, em seguida, escolha **Windows** na lista Plataforma.

   Depois de aplicar os filtros de linguagem de programação e plataforma, escolha o modelo **Aplicativo Web ASP.NET Core (.NET Core)** e, em seguida, escolha **Avançar**.

   ![Escolher o modelo de C# para o Aplicativo Web ASP.NET Core](../get-started/csharp/media/vs-2019/csharp-create-new-project-search-aspnet-core-filtered.png)

   > [!NOTE]
   > Se não vir o modelo **Aplicativo Web ASP.NET Core**, você poderá instalá-lo da janela **Criar um novo projeto**. Na mensagem **Não encontrou o que precisa?** , escolha o link **Instalar mais ferramentas e recursos**.
   >
   > ![O link 'Instalar mais ferramentas e recursos' da mensagem 'Não encontrou o que precisa?' na janela 'Criar novo projeto'](../get-started/media/vs-2019/not-finding-what-looking-for.png)
   >
   > Em seguida, no Instalador do Visual Studio, escolha a carga de trabalho de **desenvolvimento Web e ASP.NET**.
   >
   > ![Carga de trabalho do Aplicativo Web ASP.NET Core no Instalador do Visual Studio](../get-started/media/aspnet-core-web-dev-workload.png)
   >
   > Depois disso, escolha o botão **Modificar** no Instalador do Visual Studio. Pode ser solicitado que você salve seu trabalho; nesse caso, faça isso. Em seguida, escolha **Continuar** para instalar a carga de trabalho. Em seguida, retorne para a etapa 2 deste procedimento para "[Criar um projeto](#create-a-project)".

1. Na janela **Configurar seu novo projeto**, digite ou insira *OláMundo* na caixa **Nome do projeto**. Em seguida, escolha **Criar**.

   ![Na janela "Configurar seu novo projeto", dê ao projeto o nome 'OláMundo'](../get-started/csharp/media/vs-2019/csharp-name-your-aspnet-helloworld-project.png)

1. Na janela **criar um novo aplicativo Web ASP.NET Core** , verifique se **ASP.NET Core 3,0** aparece no menu suspenso superior. Em seguida, escolha **Aplicativo Web**, que inclui Razor Pages de exemplo. Em seguida, escolha **Criar**.

   ![A janela 'Criar um novo Aplicativo Web ASP.NET Core'](../get-started/csharp/media/vs-2019/csharp-create-aspnet-razor-pages-app.png)

   O Visual Studio abre seu novo projeto.

::: moniker-end

## <a name="create-and-run-the-app"></a>Criar e executar o aplicativo

::: moniker range="vs-2017"

1. No **Gerenciador de Soluções**, expanda a pasta **Páginas** e, em seguida, escolha **About.cshtml**.

   ![Escolha o arquivo About.cshtml no Gerenciador de Soluções](../ide/media/csharp-aspnet-about-page-html-file.png)

   Este arquivo corresponde a uma página chamada **Sobre** no aplicativo web, que é executada no navegador da web.

   ![A página Sobre no aplicativo Web](../ide/media/csharp-aspnet-about-page.png)

   No editor, você verá o código HTML para a área de "informações adicionais" da página **Sobre**.

   ![O código HTML para a área de informações adicionais no editor do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Altere o texto de "informações adicionais" para dizer "**Olá, Mundo!** ".

   ![Mudar o código HTML padrão para a área de informações adicionais no editor do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. No **Gerenciador de Soluções**, expanda **About.cshtml** e, em seguida, escolha **About.cshtml.cs**. (Esse arquivo também corresponde à página **Sobre** em um navegador da Web.)

   ![Escolha o arquivo About.cshtml no Gerenciador de Soluções](../ide/media/csharp-aspnet-about-page-code-file.png)

   No editor, você verá o código de C# que inclui o texto para a área "Descrição do aplicativo" da página **sobre**.

   ![O código de C# para a área de descrição do aplicativo no editor do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Alterar o texto da mensagem de "Descrição do aplicativo" para dizer "**Qual é a minha mensagem?** ".

   ![Altere o texto da mensagem padrão para a área de descrição do aplicativo no editor do Visual Studio](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Escolha **IIS Express** ou pressione **Ctrl**+**F5** para executar o aplicativo e abri-lo em um navegador da Web.

   ![Selecionar o botão IIS Express no Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Se você receber uma mensagem de erro informando **Não é possível conectar ao servidor Web 'IIS Express'** ou uma mensagem de erro que mencione um certificado SSL, feche o Visual Studio. Em seguida, abra o Visual Studio usando a opção **Executar como administrador** no menu de contexto acessado ao clicar com o botão direito do mouse. Em seguida, execute o aplicativo novamente.

1. No navegador da Web, verifique se a página **Sobre** inclui o texto atualizado.

   ![Exibir a página Sobre atualizada que inclui o texto alterado](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Feche o navegador da web.

### <a name="review-your-work"></a>Examinar seu trabalho

Exiba a animação a seguir para verificar o trabalho que você concluiu a seção anterior.

  ![Exibir o arquivo .gif animado que mostra como criar e executar um aplicativo Web ASP.NET Core C# simples no Visual Studio](../ide/media/csharp-aspnet-animated-hello-world.gif)

Parabéns por concluir este Guia de Início Rápido! Esperamos que você tenha aprendido um pouco sobre o C#, o ASP.NET Core e o IDE (ambiente de desenvolvimento integrado) do Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

1. No **Gerenciador de soluções**, expanda a pasta **páginas** e, em seguida, escolha **index. cshtml**.

   ![Escolha o arquivo index. cshtml no Gerenciador de Soluções](../ide/media/vs-2019/csharp-aspnet-index-page-cshtml-file.png)

   Esse arquivo corresponde a uma página chamada **Home** no aplicativo Web, que é executado em um navegador da Web.

   ![A página Sobre no aplicativo Web](../ide/media/vs-2019/csharp-aspnet-index-page.png)

   No editor, você verá o código HTML para o texto que aparece na **Home** Page.

   ![O código HTML no arquivo index. cshtml para a Home Page no editor do Visual Studio](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page.png)

1. Altere o texto "bem-vindo" para ler "**Olá, mundo!** ".

   ![No editor do Visual Studio, altere o código HTML padrão que diz bem-vindo para dizer Olá, Mundo em vez disso](../ide/media/vs-2019/csharp-aspnet-index-cshtml-page-hello-world.png)

1. Escolha **IIS Express** ou pressione **Ctrl**+**F5** para executar o aplicativo e abri-lo em um navegador da Web.

   ![Selecionar o botão IIS Express no Visual Studio](../ide/media/vs-2019/csharp-aspnet-generic-iisbutton.png)

   > [!NOTE]
   > Se você receber uma mensagem de erro informando **Não é possível conectar ao servidor Web 'IIS Express'** ou uma mensagem de erro que mencione um certificado SSL, feche o Visual Studio. Em seguida, abra o Visual Studio usando a opção **Executar como administrador** no menu de contexto acessado ao clicar com o botão direito do mouse. Em seguida, execute o aplicativo novamente.

1. No navegador da Web, verifique se a **Home** Page inclui o texto atualizado.

   ![Exibir a página inicial atualizada que inclui as alterações feitas](../ide/media/vs-2019/csharp-aspnet-index-page-hello-world.png)

1. Feche o navegador da web.

::: moniker-end

## <a name="next-steps"></a>Próximas etapas

Para saber mais, continue com o tutorial a seguir:

> [!div class="nextstepaction"]
> [Introdução ao C# e ao ASP.NET no Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Confira também

[Publicar seu aplicativo Web no Serviço de Aplicativo do Azure usando o Visual Studio](../deployment/quickstart-deploy-to-azure.md)
