---
title: Persistindo a propriedade de um item de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4adcf0f5c5770f5d3ffc0e0ed9bffdb108869c7f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838386"
---
# <a name="persisting-the-property-of-a-project-item"></a>Mantendo a propriedade de um item de projeto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Talvez você queira manter uma propriedade adicionada a um item de projeto, como o autor de um arquivo de origem. Você pode fazer isso armazenando a propriedade no arquivo de projeto.  
  
 A primeira etapa para manter uma propriedade em um arquivo de projeto é obter a hierarquia do projeto como uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> interface. Você pode obter essa interface usando a automação ou usando o <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection> . Depois de obter a interface, você pode usá-la para determinar qual item de projeto está selecionado no momento. Quando tiver a ID de item do projeto, você poderá usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para adicionar a propriedade.  
  
 Nos procedimentos a seguir, você mantém a propriedade VsPkg.cs `Author` com o valor `Tom` no arquivo de projeto.  
  
### <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obter a hierarquia do projeto com o objeto DTE  
  
1. Adicione o seguinte código ao seu VSPackage:  
  
    ```csharp  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    ```  
  
### <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para manter a propriedade item do projeto com o objeto DTE  
  
1. Adicione o código a seguir ao código fornecido no método no procedimento anterior:  
  
    ```csharp  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath = (string)project.ProjectItems.Item(  
            "VsPkg.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Para obter a hierarquia do projeto usando IVsMonitorSelection  
  
1. Adicione o seguinte código ao seu VSPackage:  
  
    ```csharp  
    IVsHierarchy hierarchy = null;  
    IntPtr hierarchyPtr = IntPtr.Zero;  
    IntPtr selectionContainer = IntPtr.Zero;  
    uint itemid;  
  
    // Retrieve shell interface in order to get current selection  
    IVsMonitorSelection monitorSelection =     Package.GetGlobalService(typeof(SVsShellMonitorSelection)) as     IVsMonitorSelection;  
    if (monitorSelection == null)  
        throw new InvalidOperationException();  
  
    try  
    {  
        // Get the current project hierarchy, project item, and selection container for the current selection  
        // If the selection spans multiple hierachies, hierarchyPtr is Zero  
        IVsMultiItemSelect multiItemSelect = null;  
        ErrorHandler.ThrowOnFailure(  
            monitorSelection.GetCurrentSelection(  
                out hierarchyPtr, out itemid,   
                out multiItemSelect, out selectionContainer));  
  
        // We only care if there is only one node selected in the tree  
        if (!(itemid == VSConstants.VSITEMID_NIL ||   
            hierarchyPtr == IntPtr.Zero ||  
            multiItemSelect != null ||  
            itemid == VSConstants.VSITEMID_SELECTION))  
        {  
            hierarchy = Marshal.GetObjectForIUnknown(hierarchyPtr)  
                as IVsHierarchy;  
        }  
    }  
    finally  
    {  
        if (hierarchyPtr != IntPtr.Zero)  
            Marshal.Release(hierarchyPtr);  
        if (selectionContainer != IntPtr.Zero)  
            Marshal.Release(selectionContainer);  
    }  
    ```  
  
2. 
  
### <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Para persistir a propriedade de item de projeto selecionada, dada a hierarquia do projeto  
  
1. Adicione o código a seguir ao código fornecido no método no procedimento anterior:  
  
    ```  
    IVsBuildPropertyStorage buildPropertyStorage =   
        hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");  
    }  
    ```  
  
### <a name="to-verify-that-the-property-is-persisted"></a>Para verificar se a propriedade é persistente  
  
1. Inicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o e, em seguida, abra ou crie uma solução.  
  
2. Selecione o item de projeto VsPkg.cs em **Gerenciador de soluções**.  
  
3. Use um ponto de interrupção ou determine se o VSPackage está carregado e se SetItemAttribute é executado.  
  
    > [!NOTE]
    > Você pode Autocarregar um VSPackage no contexto da interface do usuário <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid> . Para obter mais informações, consulte [carregando VSPackages](../extensibility/loading-vspackages.md).  
  
4. Feche [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e abra o arquivo de projeto no bloco de notas. Você deve ver a \<Author> marca com o valor Tom, da seguinte maneira:  
  
    ```  
    <Compile Include="VsPkg.cs">  
        <Author>Tom</Author>  
    </Compile>  
    ```  
  
## <a name="see-also"></a>Consulte Também  
 [Ferramentas personalizadas](../extensibility/internals/custom-tools.md)
