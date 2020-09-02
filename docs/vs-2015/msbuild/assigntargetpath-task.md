---
title: Tarefa AssignTargetPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 0e830e31-3bcf-4259-b2a8-a5df49b92d51
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f7bf12e9f6c90ce544205370a8ed26440388b0a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187024"
---
# <a name="assigntargetpath-task"></a>Tarefa AssignTargetPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Essa tarefa aceita arquivos de uma lista e adiciona atributos `<TargetPath>` se ainda não foram especificados.  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `AssignTargetPath`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`RootFolder`|Parâmetro de entrada de `string` opcional.<br /><br /> Contém o caminho para a pasta que contém os links de destino.|  
|`Files`|Parâmetro de entrada <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém a lista de entrada de arquivos.|  
|`AssignedFiles`|Opcional<br /><br /> <xref:Microsoft.Build.Framework.ITaskItem>`[]`parâmetro de saída.<br /><br /> Contém a lista resultante de arquivos.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir executa a tarefa `AssignTargetPath` para configurar um projeto.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="MyProject">  
        <AssignTargetPath  
RootFolder="Resources"  
            Files="@(ResourceFiles)"  
            <Output TaskParameter="AssignedFiles"  
                ItemName="OutAssignedFiles"/>  
        </AssignTargetPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefa](../msbuild/msbuild-tasks.md)   
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)
