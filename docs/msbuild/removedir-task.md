---
title: Tarefa RemoveDir | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RemoveDir
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- RemoveDir task [MSBuild]
- MSBuild, RemoveDir task
ms.assetid: 7ab214be-26b2-4bcd-9de8-c1b2091c0b74
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26a6feeca7c89a67e7dd51bd0a1f99a182ffac59
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632791"
---
# <a name="removedir-task"></a>Tarefa RemoveDir

Remove os diretórios especificados e todos os seus arquivos e subdiretórios.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `RemoveDir`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`Directories`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica os diretórios que serão excluídos.|
|`RemovedDirectories`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Contém os diretórios que foram excluídos com êxito.|

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir remove os diretórios especificados pelas propriedades `OutputDirectory` e `DebugDirectory`. Esses caminhos são tratados como relativos ao diretório do projeto.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2005">

    <PropertyGroup>
        <OutputDirectory>\Output\</OutputDirectory>
        <DebugDirectory>\Debug\</DebugDirectory>
    </PropertyGroup>

    <Target Name="RemoveDirectories">
        <RemoveDir
            Directories="$(OutputDirectory);$(DebugDirectory)" />
    </Target>

</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
