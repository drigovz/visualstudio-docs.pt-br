---
title: Tarefa GetFrameworkSdkPath | Microsoft Docs
description: Saiba mais sobre como usar a tarefa MSBuild GetFrameworkSdkPath para recuperar o caminho para o SDK do Windows.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c0fe468f593d085c10f8d077246af6858d0571fe
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914632"
---
# <a name="getframeworksdkpath-task"></a>Tarefa GetFrameworkSdkPath

Recupera o caminho para o SDK (Software Development Kit) do Windows.
## <a name="task-parameters"></a>Parâmetros de tarefa

A tabela a seguir descreve os parâmetros da tarefa `GetFrameworkSdkPath`.
A tabela a seguir descreve os parâmetros da tarefa `GetFrameworkSdkPath`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`FrameworkSdkVersion20Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 2.0, se presente. Caso contrário, retornará `String.Empty`.|
|`FrameworkSdkVersion35Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 3.5, se presente. Caso contrário, retornará `String.Empty`.|
|`FrameworkSdkVersion40Path`|Parâmetro de saída opcional somente leitura `String`.<br /><br /> Retorna o caminho para o SDK do .NET versão 4.0, se presente. Caso contrário, retornará `String.Empty`.|
|`Path`|Parâmetro de saída `String` opcional.<br /><br /> Contém o caminho para o SDK mais recente do .NET, se houver qualquer versão. Caso contrário, retornará `String.Empty`.|

## <a name="remarks"></a>Comentários

Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

O exemplo a seguir usa a `GetFrameworkSdkPath` tarefa para armazenar o caminho para o SDK do Windows na `SdkPath` propriedade.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="GetPath">
        <GetFrameworkSdkPath>
            <Output
                TaskParameter="Path"
                PropertyName="SdkPath" />
        </GetFrameworkSdkPath>
        <Message Text="$(SdkPath)"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
