---
title: Tarefa ParallelCustomBuild | Microsoft Docs
description: Saiba como o MSBuild usa a tarefa ParallelCustomBuild para executar instâncias paralelas da tarefa CustomBuild.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f4491d0a5e9c9d3a2554bd32211fd1fa8f7be2d2
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048889"
---
# <a name="parallelcustombuild-task"></a>Tarefa ParallelCustomBuild

Executar instâncias paralelas da [tarefa CustomBuild](../msbuild/custombuild-task.md).

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **ParallelCustomBuild** .

|Parâmetro|Descrição|
|---------------|-----------------|
|**BreakOnFirstFailure**|Parâmetro opcional **bool** .|
|**MaxItemsInBatch**|Parâmetro **int** opcional.|
|**MaxProcesses**|Parâmetro **int** opcional.|
|**Fontes**|Parâmetro **ITaskItem []** necessário.|

## <a name="see-also"></a>Veja também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)