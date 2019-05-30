---
title: Adicionando um atributo a um Item de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8524ebc866d92cfe39a19dc79165da7c38025628
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352377"
---
# <a name="add-an-attribute-to-a-project-item"></a>Adicionar um atributo a um item de projeto
Os métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> obter e definir o valor dos atributos de um item de projeto. SetItemAttribute cria o atributo se ele ainda não existir, adicioná-lo para os metadados de item de projeto.

## <a name="add-an-attribute-to-a-project-item"></a>Adicionar um atributo a um item de projeto

- O código a seguir usa o <xref:EnvDTE.DTE> objeto de automação e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> método para adicionar um atributo a um item de projeto. A ID do item de projeto é obtida do nome de item de projeto "program.cs". O atributo "MyAttribute" é adicionado a este item de projeto e recebe o valor "MyValue".

    ```csharp
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));
    EnvDTE.Project project = dte.Solution.Projects.Item(1);

    string uniqueName = project.UniqueName;
    IVsSolution solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));
    IVsHierarchy hierarchy;
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;
    if (buildPropertyStorage != null)
    {
        uint itemId;
        string fullPath = (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;
        hierarchy.ParseCanonicalName(fullPath, out itemId);
        buildPropertyStorage.SetItemAttribute(itemId, "MyAttribute", "MyValue");
    }

    ```

## <a name="see-also"></a>Consulte também
- [Manter os dados no arquivo de projeto MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
