---
title: Estendendo a janela de saída | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711651"
---
# <a name="extend-the-output-window"></a>Estender a janela de saída
A **janela Saída** é um conjunto de painéis de texto de leitura/gravação. O Visual Studio possui esses painéis embutidos: **Build**, em que projetos [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comunicam mensagens sobre construções, e **General**, em que comunica mensagens sobre o IDE. Os projetos recebem **Build** uma referência ao painel <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Build automaticamente através dos métodos de interface, <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> e o Visual Studio oferece acesso direto ao painel **Geral** através do serviço. Além dos painéis embutidos, você pode criar e gerenciar seus próprios painéis personalizados.

 Você pode controlar a janela <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> **Saída** diretamente através das interfaces e. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, que é <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> oferecida pelo serviço, define métodos para criar, recuperar e destruir painéis de janela **de saída.** A <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interface define métodos para mostrar painéis, esconder painéis e manipular seu texto. Uma maneira alternativa de controlar a <xref:EnvDTE.OutputWindow> janela <xref:EnvDTE.OutputWindowPane> **de saída** é através dos objetos e objetos no modelo de objeto visual studio automação. Esses objetos encapsulam quase todas <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> as <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> funcionalidades das interfaces. Além disso, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> os objetos adicionam alguma funcionalidade de nível mais alto para facilitar a enumeração dos painéis da janela **de saída** e recuperar texto dos painéis.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Crie uma extensão que use o painel Saída
 Você pode fazer uma extensão que exercita diferentes aspectos do painel de saída.

1. Crie um projeto `TestOutput` VSIX nomeado com um comando de menu chamado **TestOutput**. Para obter mais informações, consulte [Criar uma extensão com um comando menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Adicione as seguintes referências:

    1. Envdte

    2. EnvDTE80

3. Em *TestOutput.cs,* adicione a seguinte declaração usando:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. Em *TestOutput.cs,* `ShowMessageBox` exclua o método. Adicione o seguinte stub de método:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. No construtor TestOutput, altere o manipulador de comando para OutputCommandHandler. Aqui está a parte que adiciona os comandos:

    ```csharp
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
    if (commandService != null)
    {
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
        EventHandler eventHandler = OutputCommandHandler;
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
        commandService.AddCommand(menuItem);
    }
    ```

6. As seções abaixo têm diferentes métodos que mostram diferentes maneiras de lidar com o painel de saída. Você pode chamar esses métodos `OutputCommandHandler()` para o corpo do método. Por exemplo, o código `CreatePane()` a seguir adiciona o método dado na próxima seção.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Criar uma janela de saída com iVsOutputWindow
 Este exemplo mostra como criar um novo painel <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> de janela de **saída** usando a interface.

```csharp
void CreatePane(Guid paneGuid, string title,
    bool visible, bool clearWithSolution)
{
    IVsOutputWindow output =
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));
    IVsOutputWindowPane pane;

    // Create a new pane.
    output.CreatePane(
        ref paneGuid,
        title,
        Convert.ToInt32(visible),
        Convert.ToInt32(clearWithSolution));

    // Retrieve the new pane.
    output.GetPane(ref paneGuid, out pane);

     pane.OutputString("This is the Created Pane \n");
}
```

 Se você adicionar este método à extensão dada na seção anterior, ao clicar no comando **Invocar testOutput,** você verá a janela **Saída** com um cabeçalho que diz **Mostrar saída de: CreatedPane** e as palavras **Este é o painel Criado** no próprio painel.

## <a name="create-an-output-window-with-outputwindow"></a>Criar uma janela de saída com outputwindow
 Este exemplo mostra como criar um painel <xref:EnvDTE.OutputWindow> de janela de **saída** usando o objeto.

```csharp
void CreatePane(string title)
{
    DTE2 dte = (DTE2)GetService(typeof(DTE));
    OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;

    try
    {
        // If the pane exists already, write to it.
        panes.Item(title);
    }
    catch (ArgumentException)
    {
        // Create a new pane and write to it.
        panes.Add(title);
    }
}
```

 Embora <xref:EnvDTE.OutputWindowPanes> a coleção permite que você recupere um painel de janela **de saída** pelo seu título, títulos de painel não são garantidos como únicos. Quando duvidar da singularidade de um <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> título, use o método para recuperar o painel correto por seu GUID.

 Se você adicionar este método à extensão dada na seção anterior, ao clicar no comando **Invocar testOutput,** você verá a janela Saída com um cabeçalho que diz **Mostrar saída de: DTEPane** e as palavras Add **DTE Pane** no próprio painel.

## <a name="delete-an-output-window"></a>Excluir uma janela De saída
 Este exemplo mostra como excluir um painel de janela **de saída.**

```csharp
void DeletePane(Guid paneGuid)
{
    IVsOutputWindow output =
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));

    IVsOutputWindowPane pane;
    output.GetPane(ref paneGuid, out pane);

    if (pane == null)
    {
        CreatePane(paneGuid, "New Pane\n", true, true);
    }
     else
    {
        output.DeletePane(ref paneGuid);
    }
}
```

 Se você adicionar este método à extensão dada na seção anterior, ao clicar no comando **Invocar testOutput,** você verá a janela Saída com um cabeçalho que diz **Mostrar saída de: Novo painel** e as palavras **Adicionadas 'Criador',** no próprio painel. Se você clicar no comando **Invocar TestOutput** novamente, o painel será excluído.

## <a name="get-the-general-pane-of-the-output-window"></a>Obter o painel geral da janela de saída
 Este exemplo mostra como obter o painel **Geral** incorporado da janela **Saída.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Se você adicionar este método à extensão dada na seção anterior, ao clicar no comando **Invocar testOutput,** você verá que a janela **Saída** mostra as palavras **Found General pane** in the pane.

## <a name="get-the-build-pane-of-the-output-window"></a>Obtenha o painel Build da janela De saída
 Este exemplo mostra como encontrar o painel **Build** e escrever para ele. Como o painel **Build** não é ativado por padrão, ele também o ativa.

```csharp
void OutputTaskItemStringExExample(string buildMessage)
{
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));

    EnvDTE.OutputWindowPanes panes =
        dte.ToolWindows.OutputWindow.OutputWindowPanes;
    foreach (EnvDTE.OutputWindowPane pane in panes)
        {
            if (pane.Name.Contains("Build"))
            {
                pane.OutputString(buildMessage + "\n");
                pane.Activate();
                return;
             }
        }
}
```
