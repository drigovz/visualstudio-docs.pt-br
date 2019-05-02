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
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: e3393dd7e81fa98c49dd09a32457171286f88f18
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977484"
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