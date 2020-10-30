---
title: Tarefa ZipDirectory | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa ZipDirectory para criar um arquivo. zip a partir do conteúdo de um diretório.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#ZipDirectory
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ZipDirectory task [MSBuild]
- MSBuild, ZipDirectory task
ms.assetid: 916bb2e3-3017-4828-ae27-c0b5c99bbb48
caps.latest.revision: 16
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2ffdd5e2601501146f0fa21e4adb572094ddbbf
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93046621"
---
# <a name="zipdirectory-task"></a>Tarefa ZipDirectory

Cria um arquivo *.zip* do conteúdo de um diretório.

>[!NOTE]
>A tarefa `ZipDirectory` está disponível apenas no MSBuild 15.8 e superiores.

## <a name="parameters"></a>Parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `ZipDirectory`.

|Parâmetro|Descrição|
|---------------|-----------------|
|`DestinationFile`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> necessário<br /><br /> O caminho completo para o arquivo *.zip* a ser criado.|
|`Overwrite`|Parâmetro `Boolean` opcional.<br /><br /> Se `true` o arquivo de destino for substituído, se ele existir. Assume o padrão de `false`.|
|`SourceDirectory`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem> obrigatório.<br /><br /> Especifica o diretório no qual será criado um arquivo morto *.zip* .|

## <a name="remarks"></a>Comentários

 Além dos parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Exemplo

 O exemplo a seguir (se usado como um arquivo *. targets* importado) cria um arquivo *. zip* do diretório de saída após a criação de um projeto. A `$(OutputPath)` propriedade normalmente seria definida em um arquivo de projeto do MSBuild, portanto, um arquivo de projeto que importa o arquivo a seguir produziria um arquivo zip `output.zip` :

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="ZipOutputPath" AfterTargets="Build">
        <ZipDirectory
            SourceDirectory="$(OutputPath)"
            DestinationFile="$(MSBuildProjectDirectory)\output.zip" />
    </Target>

</Project>
```

## <a name="see-also"></a>Veja também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
