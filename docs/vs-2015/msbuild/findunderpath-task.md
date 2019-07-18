---
title: Tarefa FindUnderPath | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#FindUnderPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, FindUnderPath task
- FindUnderPath task [MSBuild]
ms.assetid: 3c6d58b0-36e8-47aa-bfca-b73dd2045d91
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1c679352fb8db81379ab93e800efa9f631773c36
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68149737"
---
# <a name="findunderpath-task"></a>Tarefa FindUnderPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Determina quais itens na coleção de itens especificados têm caminhos que estão dentro ou abaixo da pasta especificada.  
  
## <a name="parameters"></a>Parâmetros  
 A tabela a seguir descreve os parâmetros da tarefa `FindUnderPath`.  
  
|Parâmetro|DESCRIÇÃO|  
|---------------|-----------------|  
|`Files`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos cujos caminhos devem ser comparados com o caminho especificado pelo parâmetro `Path`.|  
|`InPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que foram encontrados no caminho especificado.|  
|`OutOfPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que não foram encontrados no caminho especificado.|  
|`Path`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o caminho da pasta a ser usada como referência.|  
|`UpdateToAbsolutePaths`|Parâmetro `Boolean` opcional.<br /><br /> Se for verdadeiro, os caminhos dos itens de saída são atualizados para ser caminhos absolutos.|  
  
## <a name="remarks"></a>Comentários  
 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, consulte [Classe base TaskExtension](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa a tarefa `FindUnderPath` para determinar se os arquivos contidos no item `MyFiles` têm caminhos existentes no caminho especificado pela propriedade `SearchPath`. Depois que a tarefa for concluída, o item `FilesNotFoundInPath` contém o arquivo `File1.txt` e o item `FilesFoundInPath` contém o arquivo `File2.txt`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <MyFiles Include="C:\File1.txt" />  
        <MyFiles Include="C:\Projects\MyProject\File2.txt" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <SearchPath>C:\Projects\MyProject</SearchPath>  
    </PropertyGroup>  
  
    <Target Name="FindFiles">  
        <FindUnderPath  
            Files="@(MyFiles)"  
            Path="$(SearchPath)">  
            <Output  
                TaskParameter="InPath"  
                ItemName="FilesFoundInPath" />  
            <Output  
                TaskParameter="OutOfPath"  
                ItemName="FilesNotFoundInPath" />  
        </FindUnderPath>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Veja também  
 [Referência de tarefas](../msbuild/msbuild-task-reference.md)   
 [Tarefas](../msbuild/msbuild-tasks.md)   
 [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
