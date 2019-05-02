---
title: Verificar subtipos de um projeto em tempo de execução | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project subtypes
- check subtypes
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3940097ac53255b7bdd2c12c9ccc64605016e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62584899"
---
# <a name="verifying-subtypes-of-a-project-at-run-time"></a>Verificando subtipos de um projeto em tempo de execução
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um VSPackage que depende de um subtipo de projeto personalizado deve incluir lógica a ser procurado para que ele pode falhar de maneira elegante se não houver o subtipo de subtipo. O procedimento a seguir mostra como verificar a presença de um subtipo especificado.  
  
### <a name="to-verify-the-presence-of-a-subtype"></a>Para verificar a presença de um subtipo de  
  
1. Obter a hierarquia do projeto dos objetos de projeto e a solução como um <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> objeto adicionando o seguinte código para o VSPackage.  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2. Converter a hierarquia para o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> interface.  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3. Obter a lista de GUIDs de tipo de projeto, invocando o <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>.  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4. Verifique a lista para o GUID do subtipo especificado.  
  
    ```  
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
