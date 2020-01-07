---
title: Tarefa FindUnderPath | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33912df490b148c91c2a0d152f979bd6149d8ae3
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75566066"
---
# <a name="findunderpath-task"></a>Tarefa FindUnderPath
Determina quais itens na coleção de itens especificados têm caminhos que estão dentro ou abaixo da pasta especificada.

## <a name="parameters"></a>Parâmetros
A tabela a seguir descreve os parâmetros da tarefa `FindUnderPath`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Files`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Especifica os arquivos cujos caminhos devem ser comparados com o caminho especificado pelo parâmetro `Path`.|
|`InPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que foram encontrados no caminho especificado.|
|`OutOfPath`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os itens que não foram encontrados no caminho especificado.|
|`Path`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o caminho da pasta a ser usada como referência.|
|`UpdateToAbsolutePaths`|Parâmetro `Boolean` opcional.<br /><br /> Se for verdadeiro, os caminhos dos itens de saída são atualizados para ser caminhos absolutos.|

## <a name="remarks"></a>Comentários
Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo
O exemplo a seguir usa a tarefa `FindUnderPath` para determinar se os arquivos contidos no item `MyFiles` têm caminhos existentes no caminho especificado pela propriedade `SearchPath`. Depois que a tarefa for concluída, o item `FilesNotFoundInPath` conterá o arquivo *File1.txt* e o item `FilesFoundInPath` conterá o arquivo *File2.txt*.

```xml
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
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
