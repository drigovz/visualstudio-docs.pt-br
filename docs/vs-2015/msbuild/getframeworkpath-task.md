---
title: Tarefa GetFrameworkPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkPath task [MSBuild]
- MSBuild, GetFrameworkPath task
ms.assetid: 5b7bcdd7-d4a0-442d-af29-8aadb3b10598
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b528d0a4971d1d070c69d12cdb9a693d9a30f20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149492"
---
# <a name="getframeworkpath-task"></a>Tarefa GetFrameworkPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Recupera o caminho para os assemblies [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
## <a name="task-parameters"></a>Parâmetros da tarefa  
 A tabela a seguir descreve os parâmetros da tarefa `GetFrameworkPath`.  
  
|Parâmetro|Descrição|  
|---------------|-----------------|  
|`FrameworkVersion11Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework versão 1.1, se estiverem presentes. Caso contrário, retornará `null`.|  
|`FrameworkVersion20Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework versão 2.0, se estiverem presentes. Caso contrário, retornará `null`.|  
|`FrameworkVersion30Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework versão 3.0, se estiverem presentes. Caso contrário, retornará `null`.|  
|`FrameworkVersion35Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework versão 3.5, se estiverem presentes. Caso contrário, retornará `null`.|  
|`FrameworkVersion40Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework versão 4.0, se estiverem presentes. Caso contrário, retornará `null`.|  
|`Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para os assemblies do framework mais recentes, se estiverem disponíveis. Caso contrário, retornará `null`.|  
  
## <a name="remarks"></a>Comentários  
 Se várias versões do [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] estiverem instaladas, essa tarefa retorna a versão na qual o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] está projetado para funcionar.  
  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `GetFrameworkPath` para armazenar o caminho para o [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] na propriedade `FrameworkPath`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="FrameworkPath" />  
        </GetFrameworkPath>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Tarefa](../msbuild/msbuild-tasks.md)   
 [Referência de tarefa](../msbuild/msbuild-task-reference.md)
