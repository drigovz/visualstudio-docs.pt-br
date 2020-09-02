---
title: Estendendo o Janela de Saída | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204431"
---
# <a name="extending-the-output-window"></a>Estendendo a Janela de Saída
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela de **saída** é um conjunto de painéis de texto de leitura/gravação. O Visual Studio tem esses painéis internos: **Build**, nos quais os projetos comunicam mensagens sobre compilações e **geral**, em que [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o comunica mensagens sobre o IDE. Os projetos obtêm uma referência ao painel de **compilação** automaticamente por meio dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> métodos de interface, e o Visual Studio oferece acesso direto ao painel **geral** por meio do <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> serviço. Além dos painéis internos, você pode criar e gerenciar seus próprios painéis personalizados.  
  
 Você pode controlar a janela de **saída** diretamente por meio das <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces e. A <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface, que é oferecida pelo <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> serviço, define métodos para criar, recuperar e destruir painéis de janela de **saída** . A <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface define métodos para mostrar painéis, ocultar painéis e manipular seu texto. Uma maneira alternativa de controlar a janela de **saída** é por meio dos <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objetos e no modelo de objeto de automação do Visual Studio. Esses objetos encapsulam quase toda a funcionalidade das <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> interfaces e. Além disso, os <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> objetos e adicionam algumas funcionalidades de nível mais alto para facilitar a enumeração dos painéis de janela de **saída** e a recuperação de texto dos painéis.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Criando uma extensão que usa o painel de saída  
 Você pode fazer uma extensão que exercita diferentes aspectos do painel de saída.  
  
1. Crie um projeto VSIX chamado `TestOutput` com um comando de menu chamado **TestOutput**. Para obter mais informações, consulte [criando uma extensão com um comando de menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Adicione as seguintes referências:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. No TestOutput.cs, adicione a seguinte instrução Using:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. Em TestOutput.cs, exclua o método de inmessagebox. Adicione o seguinte stub de método:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. No Construtor TestOutput, altere o manipulador de comandos para OutputCommandHandler. Aqui está a parte que adiciona os comandos:  
  
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
  
6. As seções a seguir têm métodos diferentes que mostram diferentes maneiras de lidar com o painel de saída. Você pode chamar esses métodos para o corpo do método OutputCommandHandler (). Por exemplo, o código a seguir adiciona o método createpane () fornecido na próxima seção.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Criando um Janela de Saída com IVsOutputWindow  
 Este exemplo mostra como criar um novo painel de janela de **saída** usando a <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> interface.  
  
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
  
 Se você adicionar esse método à extensão fornecida na seção anterior, ao clicar no comando **Invoke TestOutput** , verá a janela de **saída** com um cabeçalho que diz **Mostrar saída de: CreatedPane** e as palavras **este é o painel criado** no próprio painel.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>Criando um Janela de Saída com OutputWindow  
 Este exemplo mostra como criar um painel de janela de **saída** usando o <xref:EnvDTE.OutputWindow> objeto.  
  
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
        return panes.Add(title);  
    }  
}  
```  
  
 Embora a <xref:EnvDTE.OutputWindowPanes> coleção permita recuperar um painel de janela de **saída** por seu título, os títulos do painel não têm a garantia de serem exclusivos. Quando você dúvida sobre a exclusividade de um título, use o <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> método para recuperar o painel correto por seu GUID.  
  
 Se você adicionar esse método à extensão fornecida na seção anterior, ao clicar no comando **Invoke TestOutput** , verá a janela de saída com um cabeçalho que diz **Mostrar saída de: DTEPane** e as palavras **adicionaram o painel DTE** no próprio painel.  
  
## <a name="deleting-an-output-window"></a>Excluindo um Janela de Saída  
 Este exemplo mostra como excluir um painel de janela de **saída** .  
  
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
  
 Se você adicionar esse método à extensão fornecida na seção anterior, ao clicar no comando **Invoke TestOutput** , verá a janela de saída com um cabeçalho que indica **Mostrar saída de: New painel** e o painel de palavras **adicionadas** no próprio painel. Se você clicar no comando **Invoke TestOutput** novamente, o painel será excluído.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Obtendo o painel geral do Janela de Saída  
 Este exemplo mostra como obter o painel **geral** interno da janela de **saída** .  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Se você adicionar esse método à extensão fornecida na seção anterior, ao clicar no comando **Invoke TestOutput** , verá que a janela **saída** mostra as palavras **encontradas no painel geral** no painel.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Obtendo o painel de compilação do Janela de Saída  
 Este exemplo mostra como localizar o painel de compilação e gravar nele. Como o painel de compilação não é ativado por padrão, ele também o ativa.  
  
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
