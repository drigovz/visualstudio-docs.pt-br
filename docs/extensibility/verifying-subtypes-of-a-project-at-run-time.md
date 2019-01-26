---
title: Verificar subtipos de um projeto em tempo de execução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a64cdb11231649b49f9c0322a241c807d94fe76
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55011090"
---
# <a name="verify-subtypes-of-a-project-at-run-time"></a>Verificar subtipos de um projeto em tempo de execução
Um VSPackage que depende de um subtipo de projeto personalizado deve incluir lógica a ser procurado para que ele pode falhar de maneira elegante se não houver o subtipo de subtipo. O procedimento a seguir mostra como verificar a presença de um subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar a presença de um subtipo de  
  
1.  Obter a hierarquia de projeto dos objetos de projeto e a solução como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto adicionando o seguinte código para o VSPackage.  
  
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
  
2.  Converter a hierarquia para o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```csharp  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  Obter a lista de GUIDs de tipo de projeto, invocando o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```csharp  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  Verifique a lista para o GUID do subtipo especificado.  
  
    ```csharp  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Subtipos de projeto](../extensibility/internals/project-subtypes.md)   
 [Design de subtipos de projeto](../extensibility/internals/project-subtypes-design.md)   
 [Propriedades e métodos estendidos por subtipos do projeto](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)