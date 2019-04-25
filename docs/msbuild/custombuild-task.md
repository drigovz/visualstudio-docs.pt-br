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
ms.openlocfilehash: 197128fadb660ab06686d13ec304a5d9d1698070
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778131"
---
# <a name="custombuild-task"></a>Tarefa CustomBuild

Encapsula a ferramenta compilador do Visual C++ (cmd.exe).

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **CustomBuild**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**BuildSuffix**|Parâmetro opcional **string**.|
|**Sources**|Parâmetro obrigatório **ITaskItem[]**.|
|**TrackerLogDirectory**|Parâmetro opcional **string**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)