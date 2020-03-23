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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77272400"
---
# <a name="getoutofdateitems-task"></a>Tarefa GetOutOfDateItems

Tarefa auxiliar que lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados.

## <a name="parameters"></a>parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutOfDateItems**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**CheckForInterdependencies**|Parâmetro opcional **bool**.|
|**CommandMetadataName**|Parâmetro opcional **de string.**|
|**DependenciesMetadataName**|Parâmetro opcional **de string.**|
|**HasInterdependencies**|Parâmetro de saída **bool** opcional.|
|**OutOfDateSources**|Parâmetro de saída opcional **ITaskItem[]**.|
|**OutputsMetadataName**|Parâmetro de **corda** necessário.|
|**Fontes**|Parâmetro **opcional ITaskItem[].**|
|**TLogDirectory**|Parâmetro de **corda** necessário.|
|**TLogNamePrefix**|Parâmetro de **corda** necessário.|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)