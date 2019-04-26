---
title: Classe TrackedVCToolTask | Microsoft Docs
ms.date: 03/10/2019
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: mikeblome
ms.author: mblome
ms.workload:
- multiple
ms.openlocfilehash: 4a4044416131a27ca313d10d02404094c5f5e219
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62938863"
---
# <a name="trackedvctooltask-base-class"></a>Classe base TrackedVCToolTask

Muitas tarefas são herdadas na classe <xref:Microsoft.Build.Utilities.Task> e na classe [ToolTask](/dotnet/api/microsoft.build.utilities.tooltask). Essa classe adiciona vários parâmetros para as tarefas que derivam de [VCToolTask](../msbuild/vctooltask-base-class.md). Esses parâmetros são listados neste documento.

## <a name="parameters"></a>Parâmetros

A tabela a seguir descreve os parâmetros das classes base **TrackedVCToolTask**.

|Parâmetro|Descrição|
|---------------|-----------------|
|**DeleteOutputOnExecute**|Parâmetro opcional **bool**.|
|**EnableExecuteTool**|Parâmetro opcional **bool**.|
|**ExcludedInputPaths**|Parâmetro opcional **ITaskItem[]**.|
|**MinimalRebuildFromTracking**|Parâmetro opcional **bool**.|
|**PathOverride**|Parâmetro opcional **string**.|
|**PostBuildTrackingCleanup**|Parâmetro opcional **bool**.|
|**RootSource**|Parâmetro opcional **string**.|
|**SkippedExecution**|Parâmetro de saída **bool** opcional.|
|**SourcesCompiled**|Parâmetro de saída opcional **ITaskItem[]**.|
|**TLogCommandFile**|Parâmetro opcional **ITaskItem**.|
|**TLogReadFiles**|Parâmetro opcional **ITaskItem[]**.|
|**TLogWriteFiles**|Parâmetro opcional **ITaskItem[]**.|
|**ToolArchitecture**|Parâmetro opcional **string**.|
|**TrackCommandLines**|Parâmetro opcional **bool**.|
|**TrackFileAccess**|Parâmetro opcional **bool**.|
|**TrackedInputFilesToIgnore**|Parâmetro opcional **ITaskItem[]**.|
|**TrackedOutputFilesToIgnore**|Parâmetro opcional **ITaskItem[]**.|
|**TrackerFrameworkPath**|Parâmetro opcional **string**.|
|**TrackerSdkPath**|Parâmetro opcional **string**.|

## <a name="see-also"></a>Consulte também

[Referência de tarefas](../msbuild/msbuild-task-reference.md)<br/>
[Tarefas](../msbuild/msbuild-tasks.md)