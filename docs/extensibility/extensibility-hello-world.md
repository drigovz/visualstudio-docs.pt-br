---
title: Tutorial de extensão do Hello World | Microsoft Docs
ms.date: 03/14/2019
ms.topic: conceptual
ms.assetid: f74e1ad1-1ee5-4360-9bd5-d82467b884ca
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3beedce039d1c093b5dfebce07b09d7d3a5795dc
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194730"
---
# <a name="create-your-first-extension-hello-world"></a>Crie sua primeira extensão: Hello World

Este exemplo de Hello World explica como criar sua primeira extensão para o Visual Studio. Este tutorial mostra como adicionar um novo comando para o Visual Studio.

O processo, você aprenderá como:

* **[Criar um projeto de extensibilidade](#create-an-extensibility-project)**
* **[Adicionar um comando personalizado](#add-a-custom-command)**
* **[Modificar o código-fonte](#modify-the-source-code)**
* **[Executá-lo](#run-it)**

Neste exemplo, você usará o Visual c# para adicionar que um botão de menu personalizado chamado "Diga Hello World!" Isso se parece com isso:

![Comando do Hello World](media/hello-world-say-hello-world.png)

> [!NOTE]
> Este artigo se aplica ao Visual Studio no Windows. Para o Visual Studio para Mac, consulte [instruções passo a passo de extensibilidade no Visual Studio para Mac](/visualstudio/mac/extending-visual-studio-mac-walkthrough).

## <a name="prerequisites"></a>Pré-requisitos

Antes de começar, verifique se você instalou o **desenvolvimento de extensões do Visual Studio** carga de trabalho, que inclui o modelo VSIX, você precisará e código de exemplo.

> [!NOTE]
> Você pode usar qualquer edição do Visual Studio (Community, Professional ou Enterprise) para criar um projeto de extensibilidade do Visual Studio.

## <a name="create-an-extensibility-project"></a>Criar um projeto de extensibilidade

::: moniker range="vs-2017"

Etapa 1. No menu **Arquivo**, selecione **Novo** > **Projeto**.

Etapa 2. Na caixa de pesquisa na parte superior direita, digite "vsix" e selecione o Visual C# **projeto do VSIX**. Digite "HelloWorld" para o **nome** na parte inferior da caixa de diálogo e selecione **Okey**.

![novo projeto](media/hello-world-new-project.png)

Agora você deve ver a página de Introdução e alguns recursos de exemplo.

Se você precisar deixar este tutorial e volte a ela, você pode encontrar seu novo projeto HelloWorld na **página inicial** na **recentes** seção.

::: moniker-end

::: moniker range=">=vs-2019"

Etapa 1. No menu **Arquivo**, selecione **Novo** > **Projeto**. Pesquise por "vsix" e selecione o Visual C# **projeto do VSIX** e, em seguida **próxima**.

Etapa 2. Digite "HelloWorld" para o **nome do projeto** e selecione **criar**.

![novo projeto](media/hello-world-new-project-2019.png)

Agora você deve ver o projeto HelloWorld em **Gerenciador de soluções**.

::: moniker-end

## <a name="add-a-custom-command"></a>Adicionar um comando personalizado

Etapa 1. Se você selecionar o *.vsixmanifest* arquivo de manifesto, você pode ver quais opções estão mutáveis, como descrição, autor e versão.

Etapa 2. Clique com botão direito no projeto (não na solução). No menu de contexto, selecione **Add**e então **Novo Item**.

Etapa 3. Selecione o **extensibilidade** seção e, em seguida, escolha **comando personalizado**.

Etapa 4. No **nome** na parte inferior, insira um nome de arquivo, como *Command.cs*.

![comando personalizado](media/hello-world-custom-command.png)

O novo arquivo de comando está visível no **Gerenciador de soluções**. Sob o **recursos** nó, você encontrará outros arquivos relacionados ao seu comando. Por exemplo, se você quiser modificar a imagem, o arquivo PNG é aqui.

## <a name="modify-the-source-code"></a>Modificar o código-fonte

Neste ponto, o comando e o texto do botão são gerados automaticamente e não muito interessante. Se você quiser fazer alterações, você pode modificar o arquivo VSCT e o arquivo do CS.

* O arquivo VSCT é onde você pode renomear os comandos, bem como definir onde eles ficar no sistema de comando do Visual Studio. Conforme você explora o arquivo VSCT, você observará comentários que explicam o que cada seção dos controles de código VSCT.

* O arquivo de CS é onde você pode definir a ações, como o manipulador de clique.

::: moniker range="vs-2017"

Etapa 1. Na **Gerenciador de soluções**, localize o arquivo VSCT para seu novo comando. Nesse caso, ele será chamado *CommandPackage.vsct*.

![comando pacote vsct](media/hello-world-command-package-vsct.png)

::: moniker-end

::: moniker range=">=vs-2019"

Etapa 1. Na **Gerenciador de soluções**, localize o arquivo VSCT para seu pacote de extensão VS. Nesse caso, ele será chamado *HelloWorldPackage.vsct*.

::: moniker-end

Etapa 2. Alterar o `ButtonText` parâmetro para `Say Hello World!`.

```xml
  ...
  <Button guid="guidCommandPackageCmdSet" id="CommandId" priority="0x0100" type="Button">
     <Parent guid="guidCommandPackageCmdSet" id="MyMenuGroup" />
     <Icon guid="guidImages" id="bmpPic1" />
     <Strings>
        <ButtonText>Say Hello World!</ButtonText>
     </Strings>
  </Button>
  ...
```

Etapa 3. Volte para **Gerenciador de soluções** e localize o *Command.cs* arquivo. No `Execute` método, alterar a cadeia de caracteres `message` partir `string.Format(..)` para `Hello World!`.

```csharp
  ...
  private void Execute(object sender, EventArgs e)
  {
    ThreadHelper.ThrowIfNotOnUIThread();
    string message = "Hello World!";
    string title = "Command";

    // Show a message box to prove we were here
    VsShellUtilities.ShowMessageBox(
        this.ServiceProvider,
        message,
        title,
        OLEMSGICON.OLEMSGICON_INFO,
        OLEMSGBUTTON.OLEMSGBUTTON_OK,
        OLEMSGDEFBUTTON.OLEMSGDEFBUTTON_FIRST);
  }
  ...
```

Certifique-se de salvar suas alterações para cada arquivo.

## <a name="run-it"></a>Executá-lo

Agora você pode executar o código-fonte em que a instância Experimental do Visual Studio.

Etapa 1. Pressione **F5** para executar o **iniciar depuração** comando. Este comando compila seu projeto e inicia o depurador, iniciando uma nova instância do Visual Studio chamada a **instância Experimental**.

::: moniker range="vs-2017"

Você verá as palavras **instância Experimental** na barra de título do Visual Studio.

![barra de título da instância experimental](media/hello-world-exp-instance.png)

::: moniker-end

Etapa 2. Sobre o **ferramentas** menu da **instância Experimental**, clique em **Say Hello World!**.

![resultado final](media/hello-world-final-result.png)

Você deverá ver a saída do novo comando personalizado, neste caso, a caixa de diálogo no centro da tela que lhe dá o **Olá, mundo!** .

## <a name="next-steps"></a>Próximas etapas

Agora que você conhece os fundamentos de trabalhar com a extensibilidade do Visual Studio, aqui é onde você pode saber mais:

* [Começar a desenvolver extensões do Visual Studio](starting-to-develop-visual-studio-extensions.md) -exemplos, tutoriais. e publicar sua extensão
* [O que há de novo no SDK do Visual Studio 2017](what-s-new-in-the-visual-studio-2017-sdk.md) -novos recursos de extensibilidade do Visual Studio 2017
* [O que há de novo no SDK do Visual Studio 2019](whats-new-visual-studio-2019-sdk.md) -novos recursos de extensibilidade do Visual Studio de 2019
* [Dentro do Visual Studio SDK](internals/inside-the-visual-studio-sdk.md) -Conheça os detalhes de extensibilidade do Visual Studio