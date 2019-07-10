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
- MSBuild (Visual C++), CustomBuild task
- CustomBuild task (MSBuild (Visual C++))
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 04f33f3852f051e1f492cb2b6dca44fcdb260e11
ms.sourcegitcommit: 32144a09ed46e7223ef7dcab647a9f73afa2dd55
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/05/2019
ms.locfileid: "67587012"
---
# <a name="custombuild-task"></a>Tarefa CustomBuild

Encapsula a ferramenta compilador do Visual C++ (cmd.exe). Essa classe deriva [TrackedVCToolTask](../msbuild/trackedvctooltask-base-class.md), mas não usa o acompanhamento de arquivo para descobrir dependências de arquivo. Todas as dependências devem ser especificadas explicitamente como AdditionalDependencies para que o build incremental funcione corretamente.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **CustomBuild**.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|**BuildSuffix**|Parâmetro opcional **string**.|
|**Sources**|Parâmetro obrigatório **ITaskItem[]** .|
|**TrackerLogDirectory**|Parâmetro opcional **string**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)
