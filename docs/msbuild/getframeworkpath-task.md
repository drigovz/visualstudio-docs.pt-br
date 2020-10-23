---
title: Tarefa GetFrameworkPath | Microsoft Docs
description: Saiba como usar a tarefa MSBuild GetFrameworkPath para recuperar o caminho para os assemblies de .NET Framework.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d54a1029805066f5477cb552f5fcf3f2e09598b
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436840"
---
# <a name="getframeworkpath-task"></a>Tarefa GetFrameworkPath

Recupera o caminho para os assemblies .NET Framework.
Recupera o caminho para os assemblies .NET Framework.

## <a name="task-parameters"></a>Parâmetros de tarefa

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

Se várias versões do .NET Framework estiverem instaladas, essa tarefa retornará a versão em que o MSBuild foi projetado para ser executado.

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa a tarefa `GetFrameworkPath` para armazenar o caminho para o .NET Framework na propriedade `FrameworkPath`.

```xml
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

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
