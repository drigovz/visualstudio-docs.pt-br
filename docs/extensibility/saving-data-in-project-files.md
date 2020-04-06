---
title: Salvando dados em arquivos de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], saving in project files
- project files
- project files, saving data
ms.assetid: a3d4b15b-a91e-41ba-b235-e62632d11bc5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5fd6cfaa450bc268665ae0f58109c99002da6152
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701349"
---
# <a name="save-data-in-project-files"></a>Salvar dados em arquivos de projeto
Um subtipo de projeto pode salvar e recuperar dados específicos do subtipo no arquivo do projeto. O MPF (Managed Package Framework, estrutura de pacotes gerenciados) fornece duas interfaces para realizar essa tarefa:

- A <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> interface permite acessar valores de propriedade da seção **MSBuild** do arquivo do projeto. Os métodos fornecidos por podem ser chamados por <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage> qualquer usuário sempre que o usuário precisar carregar ou salvar dados relacionados à construção.

- O <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> é usado para persistir dados relacionados à não-compilação em XML de forma livre. Os métodos fornecidos <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> por [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] são chamados por sempre que necessário para persistir dados relacionados à não-compilação no arquivo do projeto.

  Para obter mais informações sobre como persistir dados relacionados à compilação e não-construção, consulte [Persistir dados no arquivo do projeto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md).

## <a name="save-and-retrieve-build-related-data"></a>Salvar e recuperar dados relacionados à compilação

### <a name="to-save-a-build-related-data-in-the-project-file"></a>Para salvar um dado relacionado à compilação no arquivo do projeto

- Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetPropertyValue%2A> o método para salvar um caminho completo do arquivo do projeto.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string newFullPath = GetNewFullPath();
    // Set a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.SetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, newFullPath));
    ```

### <a name="to-retrieve-build-related-data-from-the-project-file"></a>Para recuperar dados relacionados à compilação do arquivo do projeto

- Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetPropertyValue%2A> o método para recuperar um caminho completo do arquivo do projeto.

    ```
    private SpecializedProject project;
    IVsBuildPropertyStorage projectStorage = (IVsBuildPropertyStorage)project;
    string fullPath;
    // Get a full path of the project file.
    ErrorHandler.ThrowOnFailure(projectStorage.GetPropertyValue(
        "MSBuildProjectDirectory",
        String.Empty,
        (uint)_PersistStorageType.PST_PROJECT_FILE, out fullPath));
    ```

## <a name="save-and-retrieve-non-build-related-data"></a>Salvar e recuperar dados relacionados à não-compilação

### <a name="to-save-non-build-related-data-in-the-project-file"></a>Para salvar dados relacionados à não-compilação no arquivo do projeto

1. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.IsFragmentDirty%2A> o método para determinar se um fragmento XML foi alterado desde que foi salvo pela última vez em seu arquivo atual.

    ```
    public int IsFragmentDirty(uint storage, out int pfDirty)
    {
        pfDirty = 0;
        switch (storage)
        {
            case (uint)_PersistStorageType.PST_PROJECT_FILE:
            {
                if (isDirty)
                    pfDirty |= 1;
                break;
            }
            case (uint)_PersistStorageType.PST_USER_FILE:
            {
                // We do not store anything in the user file.
                break;
            }
        }

        // Forward the call to inner flavor(s)
        if (pfDirty == 0 && innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).IsFragmentDirty(storage, out pfDirty);

        return VSConstants.S_OK;

    }
    ```

2. Implemente <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Save%2A> o método para salvar os dados XML no arquivo do projeto.

    ```
    public int Save(ref Guid guidFlavor, uint storage, out string pbstrXMLFragment, int fClearDirty)
    {
        pbstrXMLFragment = null;

        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Create XML for our data.
                    XmlDocument doc = new XmlDocument();
                    XmlNode root = doc.CreateElement(this.GetType().Name);

                    XmlNode node = doc.CreateElement(targetsTag);
                    node.AppendChild(doc.CreateTextNode(this.TargetsToExecute));
                    root.AppendChild(node);

                    node = doc.CreateElement(updateTargetsTag);
                    node.AppendChild(doc.CreateTextNode(this.UpdateTargetList.ToString()));
                    root.AppendChild(node);

                    doc.AppendChild(root);
                    // Get XML fragment representing our data
                    pbstrXMLFragment = doc.InnerXml;

                    if (fClearDirty != 0)
                        isDirty = false;
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Save(ref guidFlavor, storage, out pbstrXMLFragment, fClearDirty);

        return VSConstants.S_OK;
    }
    ```

### <a name="to-retrieve-non-build-related-data-in-the-project-file"></a>Para recuperar dados relacionados à não-compilação no arquivo do projeto

1. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.InitNew%2A> o método para inicializar as propriedades de extensão do projeto e outros dados independentes de construção. Este método é chamado se não houver dados de configuração XML presentes no arquivo do projeto.

    ```
    public int InitNew(ref Guid guidFlavor, uint storage)
    {
        //Return,if it is our guid.
        if (IsMyFlavorGuid(ref guidFlavor))
            return VSConstants.S_OK;

        //Forward the call to inner flavor(s).
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).InitNew(ref guidFlavor, storage);

        return VSConstants.S_OK;
    ```

2. Implementar <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment.Load%2A> o método para carregar os dados XML do arquivo do projeto.

    ```
    public int Load(ref Guid guidFlavor, uint storage, string pszXMLFragment)
    {
        if (IsMyFlavorGuid(ref guidFlavor))
        {
            switch (storage)
            {
                case (uint)_PersistStorageType.PST_PROJECT_FILE:
                {
                    // Load our data from the XML fragment.
                    XmlDocument doc = new XmlDocument();
                    XmlNode node = doc.CreateElement(this.GetType().Name);
                    node.InnerXml = pszXMLFragment;
                    if (node == null
                        || node.FirstChild == null
                        || node.FirstChild.ChildNodes.Count == 0
                        || node.FirstChild.ChildNodes[0].Name != targetsTag)
                        break;
                    this.TargetsToExecute = node.FirstChild.ChildNodes[0].InnerText;

                    if (node.FirstChild.ChildNodes.Count <= 1
                        || node.FirstChild.ChildNodes[1].Name != updateTargetsTag)
                        break;
                    this.UpdateTargetList = bool.Parse(node.FirstChild.ChildNodes[1].InnerText);
                    break;
                }
                case (uint)_PersistStorageType.PST_USER_FILE:
                {
                    // We do not store anything in the user file.
                    break;
                }
            }
        }

        // Forward the call to inner flavor(s)
        if (this.innerCfg != null && this.innerCfg is IPersistXMLFragment)
            return ((IPersistXMLFragment)this.innerCfg).Load(ref guidFlavor, storage, pszXMLFragment);

        return VSConstants.S_OK;
    }
    ```

> [!NOTE]
> Todos os exemplos de código fornecidos neste tópico são partes de um exemplo maior em [amostras VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Confira também
- [Persistir dados no arquivo de projeto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
