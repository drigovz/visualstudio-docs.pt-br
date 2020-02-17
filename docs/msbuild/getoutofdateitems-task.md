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
- MSBuild (C++), GetOutOfDateItems task
- GetOutOfDateItems task (MSBuild (C++))
author: corob-msft
ms.author: corob
ms.workload:
- multiple
ms.openlocfilehash: bfa60ff0f7e4060f5725fe54bd5950d858b86a22
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77272400"
---
# <a name="getoutofdateitems-task"></a>Tarefa GetOutOfDateItems

Tarefa auxiliar que lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutOfDateItems**.

|Parâmetro|DESCRIÇÃO|
|---------------|-----------------|
|**CheckForInterdependencies**|Parâmetro opcional **bool**.|
|**CommandMetadataName**|Parâmetro **string** opcional.|
|**DependenciesMetadataName**|Parâmetro **string** opcional.|
|**HasInterdependencies**|Parâmetro de saída **bool** opcional.|
|**OutOfDateSources**|Parâmetro de saída opcional **ITaskItem[]** .|
|**OutputsMetadataName**|Parâmetro obrigatório **string**.|
|**Fontes**|Parâmetro opcional **ITaskItem[]** .|
|**TLogDirectory**|Parâmetro obrigatório **string**.|
|**TLogNamePrefix**|Parâmetro obrigatório **string**.|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)