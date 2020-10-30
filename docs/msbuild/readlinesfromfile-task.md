---
title: Tarefa ReadLinesFromFile | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa ReadLinesFromFile para ler uma lista de itens de um arquivo de texto. O arquivo deve ter um item em cada linha.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ReadLinesFromFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, ReadLinesFromFile task
- ReadLinesFromFile task [MSBuild]
ms.assetid: a18af929-b53a-4d9e-b7bf-e3d3737ee85f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ff2c43af40ea429714f0624db67c53fa46eb6427
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048776"
---
# <a name="readlinesfromfile-task"></a>Tarefa ReadLinesFromFile

Lê uma lista de itens de um arquivo de texto.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `ReadLinesFromFile`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`File`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o arquivo que será lido. O arquivo deve ter um item em cada linha.|
|`Lines`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém as linhas lidas do arquivo.|

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir usa a tarefa `ReadLinesFromFile` para criar itens de uma lista em um arquivo de texto. Os itens lidos do arquivo são armazenados na coleção de itens `ItemsFromFile`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyTextFile Include="Items.txt"/>
    </ItemGroup>

    <Target Name="ReadFromFile">
        <ReadLinesFromFile
            File="@(MyTextFile)" >
            <Output
                TaskParameter="Lines"
                ItemName="ItemsFromFile"/>
        </ReadLinesFromFile>
    </Target>

</Project>
```

## <a name="see-also"></a>Veja também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
