---
title: Tarefa FindAppConfigFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- FindAppConfigFile task [MSBuild]
- MSBuild, FindAppConfigFile task
ms.assetid: e292de3e-7482-4426-83ce-d921061808bf
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c54f3c222588cd13711c832d12f7598f0cc5e223
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634169"
---
# <a name="findappconfigfile-task"></a>Tarefa FindAppConfigFile

Localiza o arquivo *app.config*, caso haja algum, nas listas fornecidas.

## <a name="parameters"></a>parâmetros

 A tabela a seguir descreve os parâmetros da tarefa `FindAppConfigFile`.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|`AppConfigFile`|Parâmetro de saída <xref:Microsoft.Build.Framework.ITaskItem>`[]` opcional.<br /><br /> Especifica o primeiro item correspondente encontrado na lista, se houver.|
|`PrimaryList`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica a lista principal pela qual pesquisar.|
|`SecondaryList`|Parâmetro <xref:Microsoft.Build.Framework.ITaskItem>`[]` obrigatório.<br /><br /> Especifica a lista secundária pela qual pesquisar.|
|`TargetPath`|Parâmetro `String` obrigatório.<br /><br /> Especifica o valor a ser adicionado como metadados.|

## <a name="remarks"></a>Comentários

 Além de ter os parâmetros listados acima, essa tarefa herda parâmetros da classe <xref:Microsoft.Build.Tasks.TaskExtension>, que herda da classe <xref:Microsoft.Build.Utilities.Task>. Para obter uma lista desses parâmetros adicionais e suas descrições, confira [Classe base TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="see-also"></a>Confira também

- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)
