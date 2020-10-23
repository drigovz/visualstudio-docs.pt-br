---
title: Tarefa GetOutOfDateItems | Microsoft Docs
description: Use a tarefa auxiliar GetOutOfDateItems do MSBuild para ler e gravar logs de transações (TLOGs) e retornar conjuntos de itens que não estão atualizados.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 6cc80d4e1aa3580e0185460d19f78e9737b73220
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436828"
---
# <a name="getoutofdateitems-task"></a>Tarefa GetOutOfDateItems

Tarefa auxiliar que lê tlogs antigos, grava novos tlogs e retorna um conjunto de itens não atualizados.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros da tarefa **GetOutOfDateItems**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**CheckForInterdependencies**|Parâmetro opcional **bool**.|
|**CommandMetadataName**|Parâmetro de **cadeia de caracteres** opcional.|
|**DependenciesMetadataName**|Parâmetro de **cadeia de caracteres** opcional.|
|**HasInterdependencies**|Parâmetro de saída **bool** opcional.|
|**OutOfDateSources**|Parâmetro de saída opcional **ITaskItem[]**.|
|**OutputsMetadataName**|Parâmetro de **cadeia de caracteres** necessário.|
|**Fontes**|Parâmetro opcional **ITaskItem []** .|
|**TLogDirectory**|Parâmetro de **cadeia de caracteres** necessário.|
|**TLogNamePrefix**|Parâmetro de **cadeia de caracteres** necessário.|

## <a name="see-also"></a>Confira também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)