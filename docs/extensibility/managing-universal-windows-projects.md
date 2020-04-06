---
title: Gerenciamento de Projetos Universais de Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 47926aa1-3b41-410d-bca8-f77fc950cbe7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fbbf9b6aaf983bb36291611a7b9b50f7886915b7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702692"
---
# <a name="manage-universal-windows-projects"></a>Gerenciar projetos universais do Windows

Os aplicativos Universais windows são aplicativos que visam tanto o Windows 8.1 quanto o Windows Phone 8.1, permitindo que os desenvolvedores usem código e outros ativos em ambas as plataformas. O código e os recursos compartilhados são mantidos em um projeto compartilhado, enquanto o código e os recursos específicos da plataforma são mantidos em projetos separados, um para Windows e outro para o Windows Phone. Para obter mais informações sobre aplicativos universais do Windows, consulte [aplicativos Universais do Windows](https://msdn.microsoft.com/library/windows/apps/dn609832.aspx). As extensões do Visual Studio que gerenciam projetos devem estar cientes de que os projetos universais de aplicativos do Windows têm uma estrutura diferente dos aplicativos de plataforma única. Este passo a passo mostra como navegar no projeto compartilhado e gerenciar os itens compartilhados.

## <a name="prerequisites"></a>Pré-requisitos

A partir do Visual Studio 2015, você não instala o Visual Studio SDK a partir do centro de downloads. Está incluído como um recurso opcional na configuração do Visual Studio. Você também pode instalar o VS SDK mais tarde. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="navigate-the-shared-project"></a>Navegue pelo projeto compartilhado

1. Crie um projeto C# VSIX chamado **TestUniversalProject**. (**File** > **New** > **Project** e, em seguida, **C#** > **Extensibility** > Visual Studio**Package**). Adicione um modelo de item de projeto **de comando personalizado** (no Solution **Explorer,** clique com o botão direito do mouse no nó do projeto e selecione **Adicionar** > **novo item,** depois vá para **Extensibility**). Nomeie o arquivo **TestUniversalProject**.

2. Adicione uma referência ao *Microsoft.VisualStudio.Shell.Interop.12.1.DesignTime.dll* e *microsoft.visualStudio.Shell.Interop.14.0.DesignTime.dll* (na seção **Extensões).**

3. Abra *TestUniversalProject.cs* e `using` adicione as seguintes diretivas:

    ```csharp
    using EnvDTE;
    using EnvDTE80;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.PlatformUI;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    using System.Collections.Generic;
    using System.IO;
    using System.Windows.Forms;
    ```

4. Na `TestUniversalProject` classe, adicione um campo privado apontando para a **janela Saída.**

    ```csharp
    public sealed class TestUniversalProject
    {
        IVsOutputWindowPane output;
    . . .
    }
    ```

5. Defina a referência ao painel de saída dentro do construtor TestUniversalProject:

    ```csharp
    private TestUniversalProject(Package package)
    {
        if (package == null)
        {
            throw new ArgumentNullException("package");
        }

        this.package = package;

        OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;
        if (commandService != null)
        {
            CommandID menuCommandID = new CommandID(MenuGroup, CommandId);
            EventHandler eventHandler = this.ShowMessageBox;
            MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);
            commandService.AddCommand(menuItem);
        }
        // get a reference to the Output window
                    output = (IVsOutputWindowPane)ServiceProvider.GetService(typeof(SVsGeneralOutputWindowPane));
    }
    ```

6. Remova o código existente `ShowMessageBox` do método:

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
    }
    ```

7. Obtenha o objeto DTE, que usaremos para vários propósitos diferentes neste passo a passo. Além disso, certifique-se de que uma solução esteja carregada quando o botão de menu estiver clicado.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (EnvDTE.DTE)this.ServiceProvider.GetService(typeof(EnvDTE.DTE));
        if (dte.Solution != null)
        {
            . . .
        }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

8. Encontre o projeto compartilhado. O projeto compartilhado é um recipiente puro; não constrói ou produz saídas. O método a seguir encontra o primeiro projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> compartilhado na solução procurando o objeto que possui a capacidade de projeto compartilhado.

    ```csharp
    private IVsHierarchy FindSharedProject()
    {
        var sln = (IVsSolution)this.ServiceProvider.GetService(typeof(SVsSolution));
        Guid empty = Guid.Empty;
        IEnumHierarchies enumHiers;

        //get all the projects in the solution
        ErrorHandler.ThrowOnFailure(sln.GetProjectEnum((uint)__VSENUMPROJFLAGS.EPF_LOADEDINSOLUTION, ref empty, out enumHiers));
        foreach (IVsHierarchy hier in ComUtilities.EnumerableFrom(enumHiers))
        {
            if (PackageUtilities.IsCapabilityMatch(hier, "SharedAssetsProject"))
            {
                return hier;
            }
        }
        return null;
    }
    ```

9. No `ShowMessageBox` método, saída a legenda (o nome do projeto que aparece no **Solution Explorer**) do projeto compartilhado.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Found shared project: {0}\n", sharedCaption));
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
                }
        else
        {
            MessageBox.Show("No solution is open");
            return;
        }
    }
    ```

10. Obtenha o projeto de plataforma ativa. Projetos de plataforma são os projetos que contêm código e recursos específicos da plataforma. O método a seguir <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy> usa o novo campo para obter o projeto de plataforma ativa.

    ```csharp
    private IVsHierarchy GetActiveProjectContext(IVsHierarchy hierarchy)
    {
        IVsHierarchy activeProjectContext;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, out activeProjectContext))
        {
            return activeProjectContext;
        }
        else
        {
            return null;
        }
    }
    ```

11. No `ShowMessageBox` método, saída a legenda do projeto da plataforma ativa.

    ```csharp
    private void ShowMessageBox(object sender, EventArgs e)
    {
        var dte = (DTE)this.ServiceProvider.GetService(typeof(DTE));

        if (dte.Solution != null)
        {
            var sharedHier = this.FindSharedProject();
            if (sharedHier != null)
            {
                string sharedCaption = HierarchyUtilities.GetHierarchyProperty<string>(sharedHier, (uint)VSConstants.VSITEMID.Root,
                     (int)__VSHPROPID.VSHPROPID_Caption);
                output.OutputStringThreadSafe(string.Format("Shared project: {0}\n", sharedCaption));

                var activePlatformHier = this.GetActiveProjectContext(sharedHier);
                if (activePlatformHier != null)
                {
                    string activeCaption = HierarchyUtilities.GetHierarchyProperty<string>(activePlatformHier,
                         (uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_Caption);
                    output.OutputStringThreadSafe(string.Format("Active platform project: {0}\n", activeCaption));
                }
                else
                {
                MessageBox.Show("Shared project has no active platform project");
                }
            }
            else
            {
                MessageBox.Show("Solution has no shared project");
                return;
            }
        }
        else
            {
                MessageBox.Show("No solution is open");
                return;
            }
        }
    }
    ```

12. Iterado através dos projetos da plataforma. O método a seguir obtém todos os projetos de importação (plataforma) do projeto compartilhado.

    ```csharp
    private IEnumerable<IVsHierarchy> EnumImportingProjects(IVsHierarchy hierarchy)
    {
        IVsSharedAssetsProject sharedAssetsProject;
        if (HierarchyUtilities.TryGetHierarchyProperty(hierarchy, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID7.VSHPROPID_SharedAssetsProject, out sharedAssetsProject)
            && sharedAssetsProject != null)
        {
            foreach (IVsHierarchy importingProject in sharedAssetsProject.EnumImportingProjects())
            {
                yield return importingProject;
            }
        }
    }
    ```

    > [!IMPORTANT]
    > Se o usuário abriu um projeto de aplicativo universal C++ do Windows na instância experimental, o código acima abre uma exceção. Esse é um problema conhecido. Para evitar a exceção, substitua o `foreach` bloco acima pelo seguinte:

    ```csharp
    var importingProjects = sharedAssetsProject.EnumImportingProjects();
    for (int i = 0; i < importingProjects.Count; ++i)
    {
        yield return importingProjects[i];
    }
    ```

13. No `ShowMessageBox` método, saída a legenda de cada projeto de plataforma. Insira o seguinte código após a linha que produz a legenda do projeto da plataforma ativa. Apenas os projetos de plataforma que são carregados aparecem nesta lista.

    ```csharp
    output.OutputStringThreadSafe("Platform projects:\n");

    IEnumerable<IVsHierarchy> projects = this.EnumImportingProjects(sharedHier);

    bool isActiveProjectSet = false;
    foreach (IVsHierarchy platformHier in projects)
    {
        string platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
            (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));
    }
    ```

14. Mude o projeto da plataforma ativa. O método a seguir <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>define o projeto ativo usando .

    ```csharp
    private int SetActiveProjectContext(IVsHierarchy hierarchy, IVsHierarchy activeProjectContext)
    {
        return hierarchy.SetProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID7.VSHPROPID_SharedItemContextHierarchy, activeProjectContext);
    }
    ```

15. No `ShowMessageBox` método, mude o projeto da plataforma ativa. Insira este `foreach` código dentro do bloco.

    ```csharp
    bool isActiveProjectSet = false;
    string platformCaption = null;
    foreach (IVsHierarchy platformHier in projects)
    {
        platformCaption = HierarchyUtilities.GetHierarchyProperty<string>(platformHier, (uint)VSConstants.VSITEMID.Root,
             (int)__VSHPROPID.VSHPROPID_Caption);
        output.OutputStringThreadSafe(string.Format(" * {0}\n", platformCaption));

        // if this project is neither the shared project nor the current active platform project,
        // set it to be the active project
        if (!isActiveProjectSet && platformHier != activePlatformHier)
        {
            this.SetActiveProjectContext(sharedHier, platformHier);
            activePlatformHier = platformHier;
            isActiveProjectSet = true;
        }
    }
    output.OutputStringThreadSafe("set active project: " + platformCaption +'\n');
    ```

16. Agora experimente. Pressione F5 para iniciar a instância experimental. Crie um projeto de aplicativo de hub universal C# na instância experimental (na caixa de diálogo **Do Novo Projeto,** **Visual C#** > **Windows** > **Windows 8** > **Universal** > Hub**App**). Depois que a solução for carregada, vá para o menu **Ferramentas** e clique **em Invocar TestUniversalProject**e, em seguida, verifique o texto no painel **Saída.** Você verá algo semelhante ao que se segue:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    ```

### <a name="manage-the-shared-items-in-the-platform-project"></a>Gerencie os itens compartilhados no projeto da plataforma

1. Encontre os itens compartilhados no projeto da plataforma. Os itens do projeto compartilhado aparecem no projeto da plataforma como itens compartilhados. Você não pode vê-los no **Solution Explorer,** mas você pode andar na hierarquia do projeto para encontrá-los. O método a seguir caminha pela hierarquia e coleta todos os itens compartilhados. Ele produz opcionalmente a legenda de cada item,. Os itens compartilhados são identificados <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID7.VSHPROPID_IsSharedItem>pela nova propriedade.

    ```csharp
    private void InspectHierarchyItems(IVsHierarchy hier, uint itemid, int level, List<uint> itemIds, bool getSharedItems, bool printItems)
    {
        string caption = HierarchyUtilities.GetHierarchyProperty<string>(hier, itemid, (int)__VSHPROPID.VSHPROPID_Caption);
        if (printItems)
            output.OutputStringThreadSafe(string.Format("{0}{1}\n", new string('\t', level), caption));

        // if getSharedItems is true, inspect only shared items; if it's false, inspect only unshared items
        bool isSharedItem;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID7.VSHPROPID_IsSharedItem, out isSharedItem)
            && (isSharedItem == getSharedItems))
        {
            itemIds.Add(itemid);
        }

        uint child;
        if (HierarchyUtilities.TryGetHierarchyProperty(hier, itemid, (int)__VSHPROPID.VSHPROPID_FirstChild, Unbox.AsUInt32, out child)
            && child != (uint)VSConstants.VSITEMID.Nil)
        {
            this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);

            while (HierarchyUtilities.TryGetHierarchyProperty(hier, child, (int)__VSHPROPID.VSHPROPID_NextSibling, Unbox.AsUInt32, out child)
                && child != (uint)VSConstants.VSITEMID.Nil)
            {
                this.InspectHierarchyItems(hier, child, level + 1, itemIds, isSharedItem, printItems);
            }
                    }
    }
    ```

2. No `ShowMessageBox` método, adicione o seguinte código para andar os itens de hierarquia do projeto da plataforma. Insira-o dentro do `foreach` bloco.

    ```csharp
    output.OutputStringThreadSafe("Walk the active platform project:\n");
    var sharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ```

3. Leia os itens compartilhados. Os itens compartilhados aparecem no projeto da plataforma como arquivos vinculados ocultos, e você pode ler todas as propriedades como arquivos vinculados ordinários. O código a seguir lê o caminho completo do primeiro item compartilhado.

    ```csharp
    var sharedItemId = sharedItemIds[0];
    string fullPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared item full path: {0}\n", fullPath));
    ```

4. Agora experimente. Pressione **F5** para iniciar a instância experimental. Crie um projeto de aplicativo de hub universal C# na instância experimental (na caixa de diálogo **Do Novo Projeto,** **Visual C#** > **Windows** > **8** > **Universal** > Hub**App**) vá para o menu **Ferramentas** e clique em Invocar **TestUniversalProject**e, em seguida, verifique o texto no painel De **saída.** Você verá algo semelhante ao que se segue:

    ```
    Found shared project: HubApp.Shared
    The active platform project: HubApp.Windows
    Platform projects:
     * HubApp.Windows
     * HubApp.WindowsPhone
    set active project: HubApp.WindowsPhone
    Walk the active platform project:
        HubApp.WindowsPhone
            <HubApp.Shared>
                App.xaml
                    App.xaml.cs
                Assets
                    DarkGray.png
                    LightGray.png
                    MediumGray.png
                Common
                    NavigationHelper.cs
                    ObservableDictionary.cs
                    RelayCommand.cs
                    SuspensionManager.cs
                DataModel
                    SampleData.json
                    SampleDataSource.cs
                HubApp.Shared.projitems
                Strings
                    en-US
                        Resources.resw
            Assets
                HubBackground.theme-dark.png
                HubBackground.theme-light.png
                Logo.scale-240.png
                SmallLogo.scale-240.png
                SplashScreen.scale-240.png
                Square71x71Logo.scale-240.png
                StoreLogo.scale-240.png
                WideLogo.scale-240.png
            HubPage.xaml
                HubPage.xaml.cs
            ItemPage.xaml
                ItemPage.xaml.cs
            Package.appxmanifest
            Properties
                AssemblyInfo.cs
            References
                .NET for Windows Store apps
                HubApp.Shared
                Windows Phone 8.1
            SectionPage.xaml
                SectionPage.xaml.cs
    ```

### <a name="detect-changes-in-platform-projects-and-shared-projects"></a>Detectar mudanças em projetos de plataforma e projetos compartilhados

1. Você pode usar a hierarquia e eventos de projeto para detectar alterações em projetos compartilhados, assim como você pode para projetos de plataforma. No entanto, os itens do projeto no projeto compartilhado não são visíveis, o que significa que certos eventos não disparam quando itens de projeto compartilhados são alterados.

    Considere a seqüência de eventos quando um arquivo em um projeto é renomeado:

   1. O nome do arquivo é alterado no disco.

   2. O arquivo do projeto é atualizado para incluir o novo nome do arquivo.

      Eventos de hierarquia (por exemplo) <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>geralmente acompanham as alterações exibidas na ida e nova, como no Solution **Explorer**. Eventos de hierarquia consideram uma operação de renomeação de arquivo para consistir em uma exclusão de arquivo e, em seguida, uma adição de arquivo. No entanto, quando itens invisíveis são alterados, o sistema de eventos de hierarquia é acionado um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento, mas não um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> evento. Portanto, se você renomear um arquivo em um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A>projeto de plataforma, você recebe ambos e , <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A>mas se você renomear um arquivo em um projeto compartilhado, você recebe apenas .

      Para acompanhar as alterações nos itens do projeto, você pode lidar <xref:EnvDTE.ProjectItemsEventsClass>com eventos de itens do projeto DTE (os encontrados em ). No entanto, se você estiver lidando com um grande número <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>de eventos, você pode obter um melhor desempenho lidando com os eventos em . Neste passo a passo mostramos apenas os eventos de hierarquia e os eventos dte. Neste procedimento, você adiciona um ouvinte de eventos a um projeto compartilhado e a um projeto de plataforma. Então, quando você renomear um arquivo em um projeto compartilhado e outro arquivo em um projeto de plataforma, você pode ver os eventos que são disparados para cada operação de renomeação.

      Neste procedimento, você adiciona um ouvinte de eventos a um projeto compartilhado e a um projeto de plataforma. Então, quando você renomear um arquivo em um projeto compartilhado e outro arquivo em um projeto de plataforma, você pode ver os eventos que são disparados para cada operação de renomeação.

2. Adicione um ouvinte de eventos. Adicione um novo arquivo de classe ao projeto e chame-o *de HierarchyEventListener.cs*.

3. Abra o arquivo *HierarchyEventListener.cs* e adicione as seguintes diretivas usando:

   ```csharp
   using Microsoft.VisualStudio.Shell.Interop;
   using Microsoft.VisualStudio;
   using System.IO;
   ```

4. Tenha `HierarchyEventListener` o <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>implemento da classe:

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   { }
   ```

5. Implementar os <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents>membros de , como no código abaixo.

   ```csharp
   class HierarchyEventListener : IVsHierarchyEvents
   {
       private IVsHierarchy hierarchy;
       IVsOutputWindowPane output;

       internal HierarchyEventListener(IVsHierarchy hierarchy, IVsOutputWindowPane outputWindow) {
            this.hierarchy = hierarchy;
            this.output = outputWindow;
       }

       int IVsHierarchyEvents.OnInvalidateIcon(IntPtr hIcon) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnInvalidateItems(uint itemIDParent) {
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemAdded(uint itemIDParent, uint itemIDSiblingPrev, uint itemIDAdded) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemAdded: " + itemIDAdded + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemDeleted(uint itemID) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemDeleted: " + itemID + "\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnItemsAppended(uint itemIDParent) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnItemsAppended\n");
           return VSConstants.S_OK;
       }

       int IVsHierarchyEvents.OnPropertyChanged(uint itemID, int propID, uint flags) {
           output.OutputStringThreadSafe("IVsHierarchyEvents.OnPropertyChanged: item ID " + itemID + "\n");
           return VSConstants.S_OK;
       }
   }
   ```

6. Na mesma classe adicione outro manipulador de <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>eventos para o evento DTE , que ocorre sempre que um item do projeto é renomeado.

   ```csharp
   public void OnItemRenamed(EnvDTE.ProjectItem projItem, string oldName)
   {
       output.OutputStringThreadSafe(string.Format("[Event] Renamed {0} to {1} in project {2}\n",
            oldName, Path.GetFileName(projItem.get_FileNames(1)), projItem.ContainingProject.Name));
   }
   ```

7. Inscreva-se para os eventos de hierarquia. Você precisa se inscrever separadamente para cada projeto que você está acompanhando. Adicione o seguinte `ShowMessageBox`código , um para o projeto compartilhado e outro para um dos projetos da plataforma.

   ```csharp
   // hook up the event listener for hierarchy events on the shared project
   HierarchyEventListener listener1 = new HierarchyEventListener(sharedHier, output);
   uint cookie1;
   sharedHier.AdviseHierarchyEvents(listener1, out cookie1);

   // hook up the event listener for hierarchy events on the
   active project
   HierarchyEventListener listener2 = new HierarchyEventListener(activePlatformHier, output);
   uint cookie2;
   activePlatformHier.AdviseHierarchyEvents(listener2, out cookie2);
   ```

8. Inscreva-se no evento <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed>de itens do projeto DTE . Adicione o código a seguir depois de conectar o segundo ouvinte.

   ```csharp
   // hook up DTE events for project items
   Events2 dteEvents = (Events2)dte.Events;
   dteEvents.ProjectItemsEvents.ItemRenamed += listener1.OnItemRenamed;
   ```

9. Modifique o item compartilhado. Você não pode modificar itens compartilhados em um projeto de plataforma; em vez disso, você deve modificá-los no projeto compartilhado que é o verdadeiro proprietário desses itens. Você pode obter o ID do item <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A>correspondente no projeto compartilhado com , dando-lhe o caminho completo do item compartilhado. Então você pode modificar o item compartilhado. A mudança é propagada para os projetos da plataforma.

    > [!IMPORTANT]
    > Você deve descobrir se um item do projeto é ou não um item compartilhado antes de modificá-lo.

     O método a seguir modifica o nome de um arquivo de item do projeto.

    ```csharp
    private void ModifyFileNameInProject(IVsHierarchy project, string path)
    {
        int found;
        uint projectItemID;
        VSDOCUMENTPRIORITY[] priority = new VSDOCUMENTPRIORITY[1];
        if (ErrorHandler.Succeeded(((IVsProject)project).IsDocumentInProject(path, out found, priority, out projectItemID))
            && found != 0)
        {
            var name = DateTime.Now.Ticks.ToString() + Path.GetExtension(path);
            project.SetProperty(projectItemID, (int)__VSHPROPID.VSHPROPID_EditLabel, name);
            output.OutputStringThreadSafe(string.Format("Renamed {0} to {1}\n", path,name));
        }
    }
    ```

10. Chame este método depois de `ShowMessageBox` todo o outro código para modificar o nome do arquivo o item no projeto compartilhado. Insira isso após o código que obtém o caminho completo do item no projeto compartilhado.

    ```csharp
    // change the file name of an item in a shared project
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, sharedItemIds, true, true);
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(sharedItemId, out fullPath));
    output.OutputStringThreadSafe(string.Format("Shared project item ID = {0}, full path = {1}\n", sharedItemId, fullPath));
    this.ModifyFileNameInProject(sharedHier, fullPath);
    ```

11. Compile e execute o projeto. Crie um aplicativo de hub universal C# na instância experimental, vá para o menu **Ferramentas** e clique em **Invocar TestUniversalProject**e verifique o texto no painel de saída geral. O nome do primeiro item do projeto compartilhado (esperamos que seja o arquivo *App.xaml)* <xref:EnvDTE.ProjectItemsEventsClass.ItemRenamed> deve ser alterado, e você deve ver que o evento foi acionado. Neste caso, uma vez que a renomeação *do App.xaml* faz *com que App.xaml.cs* seja renomeado também, você deve ver quatro eventos (dois para cada projeto de plataforma). (Os eventos DTE não rastreiam os itens do projeto compartilhado.) Você deve <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> ver dois eventos (um para <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> cada um dos projetos da plataforma), mas sem eventos.

12. Agora tente renomear um arquivo em um projeto de plataforma, e você pode ver a diferença nos eventos que são demitidos. Adicione o seguinte `ShowMessageBox` código após `ModifyFileName`a chamada para .

    ```csharp
    // change the file name of an item in a platform project
    var unsharedItemIds = new List<uint>();
    this.InspectHierarchyItems(activePlatformHier, (uint)VSConstants.VSITEMID.Root, 1, unsharedItemIds, false, false);

    var unsharedItemId = unsharedItemIds[0];
    string unsharedPath;
    ErrorHandler.ThrowOnFailure(((IVsProject)activePlatformHier).GetMkDocument(unsharedItemId, out unsharedPath));
    output.OutputStringThreadSafe(string.Format("Platform project item ID = {0}, full path = {1}\n", unsharedItemId, unsharedPath));

    this.ModifyFileNameInProject(activePlatformHier, unsharedPath);
    ```

13. Compile e execute o projeto. Crie um Projeto Universal C# na instância experimental, vá para o menu **Ferramentas** e clique em **Invocar TestUniversalProject**e verifique o texto no painel de saída geral. Depois que o arquivo no projeto da plataforma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemAdded%2A> for renomeado, você deve ver um evento e um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyEvents.OnItemDeleted%2A> evento. Uma vez que a alteração do arquivo fez com que nenhum outro arquivo fosse alterado, e como as alterações em itens em um projeto de plataforma não são propagadas em lugar nenhum, há apenas um de cada um desses eventos.
