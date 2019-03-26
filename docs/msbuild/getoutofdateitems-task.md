---
title: Tarefa GetOutOfDateItems | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
f1_keywords:
- vc.task.getoutofdateitems
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (Visual C++))
author: mikeblome
ms.author: Michael.Blome
ms.workload:
- multiple
ms.openlocfilehash: 668dddcd0854869c9ede7bf96c092d415f41dd17
ms.sourcegitcommit: 4ffb7be5384ad566ce46538032bf8561754c61a4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58070342"
---
# <a name="getoutofdateitems-task"></a>Tarefa GetOutOfDateItems

Tarefa auxiliar que lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutOfDateItems**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**CheckForInterdependencies**|Parâmetro opcional **bool**.|
|**CommandMetadataName**|Parâmetro opcional **string**.|
|**DependenciesMetadataName**|Parâmetro opcional **string**.|
|**HasInterdependencies**|Parâmetro de saída **bool** opcional.|
|**OutOfDateSources**|Parâmetro de saída opcional **ITaskItem[]**.|
|**OutputsMetadataName**|Parâmetro obrigatório **string**.|
|**Sources**|Parâmetro opcional **ITaskItem[]**.|
|**TLogDirectory**|Parâmetro obrigatório **string**.|
|**TLogNamePrefix**|Parâmetro obrigatório **string**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)