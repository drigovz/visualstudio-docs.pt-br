---
title: Tarefa CustomBuild | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.custombuild
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (C++), CustomBuild task
- CustomBuild task (MSBuild (C++))
author: ghogen
ms.author: ghogen
ms.workload:
- multiple
ms.openlocfilehash: d95b6e7d4197487adc13050572ac31310701c759
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595339"
---
# <a name="custombuild-task"></a>Tarefa CustomBuild

Envolve a ferramenta de compilador Microsoft C++, cmd.exe. Essa classe deriva [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mas não usa o acompanhamento de arquivo para descobrir dependências de arquivo. Todas as dependências devem ser especificadas explicitamente como AdditionalDependencies para que o build incremental funcione corretamente.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **CustomBuild**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**BuildSuffix**|Parâmetro opcional **de string.**|
|**Fontes**|Parâmetro **ITaskItem necessário[].**|
|**TrackerLogDirectory**|Parâmetro opcional **de string.**|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)
