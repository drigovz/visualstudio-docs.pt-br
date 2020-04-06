---
title: Criando uma extensão com um comando de menu | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- write a vspackage
- vspackage
- tutorials
- visual studio package
ms.assetid: f97104c8-2bcb-45c7-a3c9-85abeda8df98
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: da1be8c6e00efd5d9ac94e53bf551d82d0f17ca4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739551"
---
# <a name="create-an-extension-with-a-menu-command"></a>Crie uma extensão com um comando de menu

Este passo a passo mostra como criar uma extensão com um comando de menu que lança o Bloco de Notas.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-menu-command"></a>Crie um comando de menu

1. Crie um projeto VSIX chamado **FirstMenuCommand**. Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Quando o projeto for aberto, adicione um modelo de item de comando personalizado chamado **FirstCommand**. No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A**Extensibilidade** **Visual C#** > e selecione **Comando Personalizado**. No **campo Nome,** na parte inferior da janela, altere o nome do arquivo de comando para *FirstCommand.cs*.

3. Compile o projeto e comece a depuração.

    A instância experimental do Visual Studio aparece. Para obter mais informações sobre a instância experimental, consulte [A instância experimental](../extensibility/the-experimental-instance.md).

::: moniker range="vs-2017"

4. No caso experimental, abra a janela**Extensões e Atualizações de** **Ferramentas.** >  Você deve ver a extensão **FirstMenuCommand** aqui. (Se você abrir **extensões e atualizações** em sua instância de trabalho do Visual Studio, você não verá **FirstMenuCommand**).

::: moniker-end

::: moniker range=">=vs-2019"

4. Na instância experimental, abra a janela **Extensões** > **Gerenciar extensões.** Você deve ver a extensão **FirstMenuCommand** aqui. (Se você abrir **Extensões de gerenciamento** em sua instância de trabalho do Visual Studio, você não verá **FirstMenuCommand**).

::: moniker-end

Agora vá para o menu **Ferramentas** na instância experimental. Você deve ver o comando **Invocar FirstCommand.** Neste ponto, o comando traz uma caixa de mensagens que diz **FirstCommandPackage inside FirstMenuCommand.FirstCommand.MenuItemCallback()** Vamos ver como realmente iniciar o Bloco de Notas a partir deste comando na próxima seção.

## <a name="change-the-menu-command-handler"></a>Alterar o manipulador de comando do menu

Agora vamos atualizar o manipulador de comando para iniciar o Bloco de Notas.

1. Pare de depurar e volte para a sua instância de trabalho do Visual Studio. Abra o arquivo *FirstCommand.cs* e adicione a seguinte declaração usando:

    ```csharp
    using System.Diagnostics;
    ```

2. Encontre o construtor privado FirstCommand. É aqui que o comando é ligado ao serviço de comando e o manipulador de comando é especificado. Altere o nome do manipulador de comando para StartNotepad, da seguinte forma:

    ```csharp
    private FirstCommand(AsyncPackage package, OleMenuCommandService commandService)
    {
        this.package = package ?? throw new ArgumentNullException(nameof(package));
        commandService = commandService ?? throw new ArgumentNullException(nameof(commandService));

        CommandID menuCommandID = new CommandID(CommandSet, CommandId);
        // Change to StartNotepad handler.
        MenuCommand menuItem = new MenuCommand(this.StartNotepad, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

3. Remova `MenuItemCallback` o método `StartNotepad` e adicione um método, que apenas iniciará o Bloco de Notas:

    ```csharp
    private void StartNotepad(object sender, EventArgs e)
    {
        Process proc = new Process();
        proc.StartInfo.FileName = "notepad.exe";
        proc.Start();
    }
    ```

4. Agora experimente. Quando você começar a depurar o projeto e clicar **em Ferramentas** > **Invocar FirstCommand,** você deve ver uma instância do Bloco de Notas aparecer.

    Você pode usar uma <xref:System.Diagnostics.Process> instância da classe para executar qualquer executável, não apenas bloco de notas. Experimente com, `calc.exe`por exemplo.

## <a name="clean-up-the-experimental-environment"></a>Limpe o ambiente experimental

Se você está desenvolvendo várias extensões, ou apenas explorando resultados com diferentes versões do seu código de extensão, seu ambiente experimental pode parar de funcionar como deveria. Neste caso, você deve executar o script de reset. Chama-se **Reset the Visual Studio Experimental Instance**, e é lançado como parte do Visual Studio SDK. Este script remove todas as referências às suas extensões do ambiente experimental, para que você possa começar do zero.

Você pode chegar a este script de duas maneiras:

1. Na área de trabalho, encontre **Reset the Visual Studio Experimental Instance**.

2. Na linha de comando, execute o seguinte:

    ```xml
    <VSSDK installation>\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe /Reset /VSInstance=<version> /RootSuffix=Exp && PAUSE

    ```

## <a name="deploy-your-extension"></a>Implantar sua extensão

Agora que você tem sua extensão de ferramenta funcionando do jeito que você quer, é hora de pensar em compartilhá-la com seus amigos e colegas. Isso é fácil, desde que eles tenham o Visual Studio 2015 instalado. Tudo o que você tem que fazer é enviar-lhes o arquivo *.vsix* que você construiu. (Certifique-se de construí-lo no modo de liberação.)

Você pode encontrar o arquivo *.vsix* para esta extensão no diretório *bin FirstMenuCommand.* Especificamente, assumindo que você tenha construído a configuração de versão, ela estará em:

*\<diretório de código>\FirstMenuCommand\FirstMenu'\bin\Release\ FirstMenuCommand.vsix*

Para instalar a extensão, seu amigo precisa fechar todas as instâncias abertas do Visual Studio e, em seguida, clicar duas vezes no arquivo *.vsix,* que traz o **Instalador VSIX**. Os arquivos são copiados para o *diretório %LocalAppData%\Microsoft\VisualStudio\<>\Extensions.*

Quando seu amigo trouxer o Visual Studio novamente, eles encontrarão a extensão FirstMenuCommand em **Extensões** > **e Atualizações de Ferramentas**. Eles podem ir a **Extensões e Atualizações para desinstalar** ou desativar a extensão, também.

## <a name="next-steps"></a>Próximas etapas

Este passo a passo mostrou apenas uma pequena parte do que você pode fazer com uma extensão do Visual Studio. Aqui está uma pequena lista de outras coisas (razoavelmente fáceis) que você pode fazer com extensões do Visual Studio:

1. Você pode fazer muito mais coisas com um comando de menu simples:

   1. Adicionar seu próprio ícone: [Adicionar ícones aos comandos do menu](../extensibility/adding-icons-to-menu-commands.md)

   2. Alterar o texto do comando menu: [Altere o texto de um comando menu](../extensibility/changing-the-text-of-a-menu-command.md)

   3. Adicionar um atalho de menu a um comando: [Vincular atalhos de teclado a itens de menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)

2. Adicione diferentes tipos de comandos, menus e barras de ferramentas: [Amplie menus e comandos](../extensibility/extending-menus-and-commands.md)

3. Adicione janelas de ferramentas e amplie as janelas de ferramentas internas do Visual Studio: [amplie e personalize janelas de ferramentas](../extensibility/extending-and-customizing-tool-windows.md)

4. Adicione o IntelliSense, sugestões de código e outros recursos aos editores de código existentes: [Amplie o editor e os serviços de idioma](../extensibility/extending-the-editor-and-language-services.md)

5. Adicionar páginas de opções e propriedades e configurações do usuário à sua extensão: [Estender propriedades e a janela Propriedade](../extensibility/extending-properties-and-the-property-window.md) e estender as [configurações e opções do usuário](../extensibility/extending-user-settings-and-options.md)

   Outros tipos de extensões exigem um pouco mais de trabalho, como criar um novo tipo de projeto ([Ampliar projetos),](../extensibility/extending-projects.md)criar um novo tipo de editor[(Criar editores e designers personalizados),](../extensibility/creating-custom-editors-and-designers.md)ou implementar sua extensão em uma concha isolada: [Visual Studio shell isolado](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
