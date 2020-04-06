---
title: Obtendo propriedades do projeto | Microsoft Docs
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- project properties, displaying in tool window
- tool windows, displaying project properties
ms.assetid: 96ba07ca-0811-4013-8602-12550ac4ba79
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ddfd48827bc762c9189f9b7600cfe9200e5c866
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711409"
---
# <a name="get-project-properties"></a>Obtenha propriedades do projeto

Este passo a passo mostra como exibir propriedades do projeto em uma janela de ferramenta.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Ele está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="to-create-a-vsix-project-and-add-a-tool-window"></a>Para criar um Projeto VSIX e adicionar uma janela de ferramenta

1. Toda extensão do Visual Studio começa com um projeto de implantação vsix, que conterá os ativos de extensão. Crie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um projeto `ProjectPropertiesExtension`VSIX chamado . Você pode encontrar o modelo de projeto VSIX na caixa de diálogo **Projeto Novo** procurando por "vsix".

2. Adicione uma janela de ferramenta adicionando um `ProjectPropertiesToolWindow`modelo de item de janela de ferramenta personalizado chamado . No **Solution Explorer,** clique com o botão direito do mouse no nó do projeto e **selecione Adicionar** > **novo item**. Na **caixa de diálogo Adicionar novo item,** vá para A > **Extensibilidade** de **Itens Visuais C#** e selecione **Janela de ferramenta personalizada**. No **campo Nome** na parte inferior da caixa `ProjectPropertiesToolWindow.cs`de diálogo, altere o nome do arquivo para . Para obter mais informações sobre como criar uma janela de ferramenta personalizada, consulte [Criar uma extensão com uma janela de ferramenta](../extensibility/creating-an-extension-with-a-tool-window.md).

3. Construa a solução e verifique se ela compila sem erros.

### <a name="to-display-project-properties-in-a-tool-window"></a>Para exibir propriedades do projeto em uma janela de ferramenta

1. No arquivo ProjectPropertiesToolWindowCommand.cs, adicione as seguintes diretivas usando.

    ```csharp
    using EnvDTE;
    using System.Windows.Controls;

    ```

2. Em *ProjectPropertiesToolControl.xaml*, remova o botão existente e adicione um TreeView da caixa de ferramentas. Você também pode remover o manipulador de eventos de clique do arquivo *ProjectPropertiesToolWindowControl.xaml.cs.*

3. Em *ProjectPropertiesToolWindowCommand.cs,* `ShowToolWindow()` use o método para abrir o projeto e ler suas propriedades e, em seguida, adicione as propriedades ao TreeView. O código para ShowToolWindow deve ser parecido com o seguinte:

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        ToolWindowPane window = this.package.FindToolWindow(typeof(ProjectPropertiesToolWindow), 0, true);
        if ((null == window) || (null == window.Frame))
        {
            throw new NotSupportedException("Cannot create window.");
        }
        IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
        Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());

        // Get the tree view and populate it if there is a project open.
        ProjectPropertiesToolWindowControl control = (ProjectPropertiesToolWindowControl)window.Content;
        TreeView treeView = control.treeView;

        // Reset the TreeView to 0 items.
        treeView.Items.Clear();

        DTE dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));
        Projects projects = dte.Solution.Projects;
        if (projects.Count == 0)   // no project is open
        {
            TreeViewItem item = new TreeViewItem();
            item.Name = "Projects";
            item.ItemsSource = new string[]{ "no projects are open." };
            item.IsExpanded = true;
            treeView.Items.Add(item);
            return;
        }

        Project project = projects.Item(1);
        TreeViewItem item1 = new TreeViewItem();
        item1.Header = project.Name + "Properties";
        treeView.Items.Add(item1);

        foreach (Property property in project.Properties)
        {
            TreeViewItem item = new TreeViewItem();
            item.ItemsSource = new string[] { property.Name };
            item.IsExpanded = true;
            treeView.Items.Add(item);
        }
    }
    ```

4. Compile o projeto e comece a depuração. A instância experimental deve aparecer.

5. Na instância experimental, abra um projeto.

6. Na **exibição** > **Outros Windows** clicam em **ProjectPropertiesToolWindow**.

  Você deve ver o controle da árvore na janela da ferramenta juntamente com o nome do primeiro projeto e de todas as suas propriedades de projeto.
