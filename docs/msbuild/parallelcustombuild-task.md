---
title: Tarefa ParallelCustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.parallelcustombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 54623ab1c58d85de55c5b8a24384bf0be46f1a61
ms.sourcegitcommit: d78821f8c353e0102b1554719f549f32dffac71b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/27/2019
ms.locfileid: "58515120"
---
# <a name="parallelcustombuild-task"></a>Tarefa ParallelCustomBuild

Executar instâncias paralelas da [tarefa CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **ParallelCustomBuild**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parâmetro opcional **bool**.|
|**MaxItemsInBatch**|Parâmetro **int** opcional.|
|**MaxProcesses**|Parâmetro **int** opcional.|
|**Sources**|Parâmetro obrigatório **ITaskItem[]**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)