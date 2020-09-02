---
title: Renomeando nós de hierarquia do projeto (C++) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- HierUtil7 sample [Visual Studio SDK], renaming project nodes
- project nodes, renaming in HierUtil7 sample
ms.assetid: cea5968e-e9f8-41a5-b068-622df542247c
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: c7ad43fe1fd0e22cd94194d3079761de812b6ced
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686582"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Renomeando nós de hierarquia de projeto (C++)
Você pode renomear um nó de hierarquia de pasta de projeto usando a estrutura de projeto HierUtil7 para C++ não gerenciado. Para obter mais informações, consulte [exemplo de HierUtil7](https://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Expandindo o nó da hierarquia  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Para expandir o nó da hierarquia e renomear a pasta  
  
1. Selecione o nó hierarquia usando o seguinte método:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` é o contêiner de hierarquia correspondente à pasta e `EXPF_SelectItem` é da <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> enumeração. O `GUID_MacroExplorer` é uma constante de GUID definida em VSShell. idl e é um exemplo para `rguidPersistenceSlot` na assinatura da função de `ExtExpand` , definida em Hu_node. h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Você pode encontrar o arquivo Hu_node. h na pasta, \<installation root> \Program Files\VSIP 8.0 \ EnvSDK\common\hierutil7:  
  
2. Renomeie a pasta postando o comando rename usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` é um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ponteiro: `<IVsUIShell>``srpVsUIShell` . `guiVSStd97` é um identificador exclusivo do grupo de comandos ao qual o comando `cmdidRename` pertence, definido em Vsshlids. h.  
  
## <a name="see-also"></a>Consulte Também  
 [Criando tipos de projeto](../extensibility/internals/creating-project-types.md)   
 [Exemplos de VSSDK](../misc/vssdk-samples.md)