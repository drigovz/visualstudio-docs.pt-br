---
title: Tarefa CombinePath | Microsoft Docs
description: Saiba mais sobre como usar a tarefa MSBuild CombinePath para combinar os caminhos especificados em um único caminho.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, CombinePath task
- CombinePath task [MSBuild]
ms.assetid: c20edbf4-3d4f-4f66-b1d5-753a0d858ed8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f1eb27a311f1b61e3e36b4c9eaa65de7f3fd8f1c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939493"
---
# <a name="combinepath-task"></a>Tarefa CombinePath

Combina os caminhos especificados em um único caminho.
## <a name="task-parameters"></a>Parâmetros de tarefa

 A tabela a seguir descreve os parâmetros da [tarefa CombinePath](../msbuild/combinepath-task.md).


|Parâmetro|Descrição|
|---------------|-----------------|
|`BasePath`|Parâmetro `String` obrigatório.<br /><br /> O caminho base para combinar com os outros caminhos. Pode ser um caminho relativo, um caminho absoluto ou um espaço em branco.|
|`Paths`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Uma lista de caminhos individuais para combinar com o BasePath para formar o caminho combinado. Os caminhos podem ser relativos ou absolutos.|
|`CombinedPaths`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> O caminho combinado é criado por essa tarefa.|

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

 O exemplo a seguir mostra como criar uma estrutura de pasta de saída usando `CombinePath` o para construir a propriedade `$(OutputDirectory)` combinando um caminho raiz `$(PublishRoot)` concatenado com `$(ReleaseDirectory)` e uma lista de subpastas `$(LangDirectories)` .

 ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <PublishRoot>C:\Site1\Release</PublishRoot>
  </PropertyGroup>

  <ItemGroup>
    <LangDirectories Include="en-us\;fr-fr\"/>
  </ItemGroup>

  <Target Name="CreateOutputDirectories" AfterTargets="Build">
    <CombinePath BasePath="$(PublishRoot)" Paths="@(LangDirectories)" >
      <Output TaskParameter="CombinedPaths" ItemName="OutputDirectories"/>
    </CombinePath>
    <MakeDir Directories="@(OutputDirectories)" />
  </Target>
```

A única propriedade que `CombinePath` permite ser uma lista é `Paths` , caso em que a saída também é uma lista. Portanto, se `$(PublishRoot)` for *C:\Site1 \\* e `$(ReleaseDirectory)` for *Release \\* e `@(LangDirectories)` for *en-US \; fr-fr \\*, este exemplo criará as pastas:

- C:\Site1\Release\en-us\
- C:\Site1\Release\fr-fr\

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
