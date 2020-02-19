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
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: 0d8a171d393f629d0b6ab3a7fc61ad37862b0da1
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77279259"
---
# <a name="parallelcustombuild-task"></a>Tarefa ParallelCustomBuild

Executar instâncias paralelas da [tarefa CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **ParallelCustomBuild**.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parâmetro opcional **bool**.|
|**MaxItemsInBatch**|Parâmetro **int** opcional.|
|**MaxProcesses**|Parâmetro **int** opcional.|
|**Fontes**|Parâmetro obrigatório **ITaskItem[]** .|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)