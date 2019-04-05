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
ms.openlocfilehash: 7f6406936f293eea9c604b830f8eaab55a90a957
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "58924934"
---
# <a name="renaming-project-hierarchy-nodes-c"></a>Renomeando nós de hierarquia do projeto (C++)
Você pode renomear um nó de hierarquia de pasta do projeto, usando a estrutura do projeto HierUtil7 para C++ não gerenciado. Para obter mais informações, consulte [HierUtil7 exemplo](http://msdn.microsoft.com/29c15184-a70c-4813-86c2-fb1d47442d11).  
  
## <a name="expanding-the-hierarchy-node"></a>Expandindo o nó de hierarquia  
  
#### <a name="to-expand-the-hierarchy-node-and-rename-the-folder"></a>Para expandir o nó da hierarquia e renomeie a pasta  
  
1.  Selecione o nó da hierarquia usando o método a seguir:  
  
    ```  
    IfFailGo(pNode->ExtExpand(EXPF_SelectItem, GUID_MacroExplorer));  
    ```  
  
     `pNode` é o contêiner de hierarquia correspondente para a pasta e `EXPF_SelectItem` provém o <xref:Microsoft.VisualStudio.Shell.Interop.EXPANDFLAGS> enumeração. O `GUID_MacroExplorer` é uma constante GUID definida no Vsshell.idl e é um exemplo de `rguidPersistenceSlot` na assinatura de função de `ExtExpand`, definida em Hu_node.h.  
  
    ```  
    HRESULT ExtExpand(EXPANDFLAGS expandflags, REFGUID rguidPersistenceSlot = GUID_SolutionExplorer) const;  
    ```  
  
     Você pode encontrar o arquivo Hu_node.h na pasta, \<raiz de instalação > \Program Files\VSIP 8.0\EnvSDK\common\hierutil7:  
  
2.  Renomeie a pasta postando o comando Renomear usando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.PostExecCommand%2A>  
  
    ```  
    IfFailGo(srpVsUIShell->PostExecCommand(&guidVSStd97, cmdidRename, 0, NULL));  
    ```  
  
     `srpVsUIShell` é um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> ponteiro: `<IVsUIShell>``srpVsUIShell`. `guiVSStd97` é um identificador exclusivo do grupo de comando para o qual o comando `cmdidRename` pertence, definido em Vsshlids.h.  
  
## <a name="see-also"></a>Consulte também  
 [Criar tipos de projeto](../extensibility/internals/creating-project-types.md)   
 [Exemplos de VSSDK](../misc/vssdk-samples.md)