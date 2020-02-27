---
title: Tarefa RemoveDuplicates | Microsoft Docs
ms.date: 03/01/2018
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDuplicates
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RemoveDuplicates task
- RemoveDuplicates task [MSBuild]
ms.assetid: 481cbab6-73ff-488c-aba5-2c09f9eb1e04
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 90366bab14eefd1be4edac81d6b09b3f57aa3332
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632778"
---
# <a name="removeduplicates-task"></a>Tarefa RemoveDuplicates

Remove itens duplicados da coleção do item especificado.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `RemoveDuplicates`.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`Filtered`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém uma coleção de itens com todos os itens duplicados removidos. A ordem dos itens de entrada é preservada, mantendo a primeira instância de cada item duplicado.|
|`Inputs`|Parâmetro opcional <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Coleção de itens do qual remover itens duplicados.|

## <a name="remarks"></a>Comentários

 Esta tarefa não diferencia maiusculas de minúsculas e não compara os metadados do item ao determinar as duplicatas.

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir usa a tarefa `RemoveDuplicates` para remover itens duplicados da `MyItems` coleção de itens. Quando a tarefa for concluída, a coleção de item `FilteredItems` contém um item.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile.cs"/>
        <MyItems Include="MyFile.cs">
            <Culture>fr</Culture>
        </MyItems>
        <MyItems Include="myfile.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

 O exemplo a seguir mostra que a tarefa `RemoveDuplicates` preserva a ordem de entrada. Após a conclusão da tarefa, a coleção de itens `FilteredItems` conterá os itens *MyFile2.cs*, *MyFile1.cs* e *MyFile3.cs*, nessa ordem.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyItems Include="MyFile2.cs"/>
        <MyItems Include="MyFile1.cs" />
        <MyItems Include="MyFile3.cs" />
        <MyItems Include="myfile1.cs"/>
    </ItemGroup>

    <Target Name="RemoveDuplicateItems">
        <RemoveDuplicates
            Inputs="@(MyItems)">
            <Output
                TaskParameter="Filtered"
                ItemName="FilteredItems"/>
        </RemoveDuplicates>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
- [Conceitos do MSBuild](../msbuild/msbuild-concepts.md)
- [Tarefas](../msbuild/msbuild-tasks.md)
