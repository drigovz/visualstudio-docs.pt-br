---
title: Verificando subtipos de um projeto em tempo de execução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0d739a9f8734dd8941e3254d03364cbf4c77350
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698178"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificar subtipos de um projeto em tempo de execução
Um VSPackage que depende de um subtipo de projeto personalizado deve incluir a lógica de procurar esse subtipo para que ele possa falhar graciosamente se o subtipo não estiver presente. O procedimento a seguir mostra como verificar a presença de um subtipo especificado.

### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar a presença de um subtipo

1. Obtenha a hierarquia do projeto dos objetos de projeto e solução como objeto, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> adicionando o seguinte código ao seu VSPackage.

    ```csharp
    EnvDTE.DTE dte;
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));

    EnvDTE.Project project;
    project = dte.Solution.Projects.Item(1);

    IVsSolution solution;
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));

    IVsHierarchy hierarchy;
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);

    ```

2. Lance a hierarquia <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> para a interface.

    ```csharp
    IVsAggregatableProjectCorrected AP;
    AP = hierarchy as IVsAggregatableProjectCorrected;

    ```

3. Obtenha a lista de GUIDs do <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>tipo projeto invocando o .

    ```csharp
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();

    ```

4. Verifique a lista para o GUID do subtipo especificado.

    ```csharp
    // Replace the string "MyGUID" with the GUID of the subtype.
    string guidMySubtype = "MyGUID";
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)
    {
        // The specified subtype is present.
    }
    ```

## <a name="see-also"></a>Confira também
- [Subtipos do projeto](../extensibility/internals/project-subtypes.md)
- [Projeto de subtipos](../extensibility/internals/project-subtypes-design.md)
- [Propriedades e métodos estendidos por subtipos de projetos](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)
