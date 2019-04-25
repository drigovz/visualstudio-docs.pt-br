---
title: Tarefa CombinePath | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b73ddd4715d3abd29f87d7ef38a269d821733ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62569713"
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

## <a name="see-also"></a>Consulte também
- [Tarefas](../msbuild/msbuild-tasks.md)
- [Referência de tarefas](../msbuild/msbuild-task-reference.md)