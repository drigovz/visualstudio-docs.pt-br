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
- MSBuild (C++), ParallelCustomBuild task
- ParallelCustomBuild task (MSBuild (C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: c6ea14e61eb2d62f3fc9ccdac3a17010ccc9194f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747220"
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
|**Sources**|Parâmetro obrigatório **ITaskItem[]** .|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)