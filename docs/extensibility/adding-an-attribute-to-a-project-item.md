---
title: Adicionando um atributo a um item de projeto | Microsoft Docs
description: Saiba como adicionar um atributo a um item de projeto no Visual Studio usando os métodos de interoperabilidade do Shell GetItemAttribute e SetItemAttribute.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- attributes [Visual Studio], adding to a project item
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d43745155193baadc87784c0e99123461dda1eed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951310"
---
# <a name="add-an-attribute-to-a-project-item"></a>Adicionar um atributo a um item de projeto
Os métodos <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> Get e definem o valor dos atributos de um item de projeto. SetItemAttribute criará o atributo se ele ainda não existir, adicionando-o aos metadados do item de projeto.

## <a name="add-an-attribute-to-a-project-item"></a>Adicionar um atributo a um item de projeto

- O código a seguir usa o <xref:EnvDTE.DTE> objeto Automation e o <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A> método para adicionar um atributo a um item de projeto. A ID do item de projeto é obtida do nome do item de projeto "program.cs". O atributo "MyAttribute" é adicionado a este item de projeto e recebe o valor "MyValue".

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
- [Manter dados no arquivo de projeto do MSBuild](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)
