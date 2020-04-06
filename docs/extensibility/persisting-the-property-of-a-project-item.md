---
title: Persistindo a Propriedade de um Item do Projeto | Microsoft Docs
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- properties, adding to a project item
- project items, adding properties
ms.assetid: d7a0f2b0-d427-4d49-9536-54edfb37c0f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15c280f15436a5e27bcc0dcc4d2fb9e9bdd82933
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702203"
---
# <a name="persist-the-property-of-a-project-item"></a>Persistir a propriedade de um item de projeto
Você pode querer persistir uma propriedade que você adiciona a um item do projeto, como o autor de um arquivo de origem. Você pode fazer isso armazenando a propriedade no arquivo do projeto.

 O primeiro passo para persistir uma propriedade em um arquivo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> projeto é obter a hierarquia do projeto como uma interface. Você pode obter esta interface usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>automação ou usando . Uma vez que você obtenha a interface, você pode usá-la para determinar qual item do projeto está atualmente selecionado. Uma vez que você tenha o id do item do projeto, você pode usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> para adicionar a propriedade.

 Nos procedimentos a seguir, `Author` você persiste o *VsPkg.cs* propriedade com o valor `Tom` no arquivo do projeto.

## <a name="to-obtain-the-project-hierarchy-with-the-dte-object"></a>Para obter a hierarquia do projeto com o objeto DTE

1. Adicione o seguinte código ao seu VSPackage:

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    ```

## <a name="to-persist-the-project-item-property-with-the-dte-object"></a>Para persistir a propriedade do item do projeto com o objeto DTE

1. Adicionar o seguinte código ao código dado no método no procedimento anterior:

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

## <a name="to-obtain-the-project-hierarchy-using-ivsmonitorselection"></a>Para obter a hierarquia do projeto usando iVsMonitorSelection

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

## <a name="to-persist-the-selected-project-item-property-given-the-project-hierarchy"></a>Para persistir a propriedade do item do projeto selecionado, dada a hierarquia do projeto

1. Adicionar o seguinte código ao código dado no método no procedimento anterior:

    ```csharp
    IVsBuildPropertyStorage buildPropertyStorage =
        hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        buildPropertyStorage.SetItemAttribute(itemId, "Author", "Tom");
    }
    ```

## <a name="to-verify-that-the-property-is-persisted"></a>Para verificar se a propriedade é persistida

1. Inicie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e depois abra ou crie uma solução.

2. Selecione o item do projeto VsPkg.cs no **Solution Explorer**.

3. Use um ponto de ruptura ou determine de outra forma que seu VSPackage está carregado e que SetItemAttribute é executado.

   > [!NOTE]
   > Você pode carregar automaticamente um VSPackage <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_guid>no contexto de Interface do UI . Para obter mais informações, consulte [Load VSPackages](../extensibility/loading-vspackages.md).

4. Feche [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e abra o arquivo do projeto no Bloco de Notas. Você deve \<ver o Autor> tag com o valor Tom, da seguinte forma:

   ```xml
   <Compile Include="VsPkg.cs">
       <Author>Tom</Author>
   </Compile>
   ```

## <a name="see-also"></a>Confira também

- [Ferramentas personalizadas](../extensibility/internals/custom-tools.md)
